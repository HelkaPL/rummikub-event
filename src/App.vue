<template>
  <div class="container">
    <h1 class="title">Wielkie odliczanie !!!</h1>
    <div class="timer">
      <div class="labels">
        <p class="tile">DNI</p>
        <p class="tile">GODZINY</p>
        <p class="tile">MINUTY</p>
        <p class="tile">SEKUNDY</p>
      </div>
      <div class="tiles">
        <div class="tile"><span>{{ daysLeft }}</span></div>
        <div class="tile"><span>{{ hoursLeft }}</span></div>
        <div class="tile"><span>{{ minutesLeft }}</span></div>
        <div class="tile"><span>{{ secondsLeft }}</span></div>
      </div>
    </div>
    <div class="bottom">
      <img class="image-left" src="@/assets/logoR.png" alt="Rummikube Logo R"/>
      <img class="image-center" src="@/assets/event.png " alt="event banner" />
      <img class="image-right" src="@/assets/face.png" alt="rummi-logo-face"/>
    </div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'App',
  data() {
    return {
      endTime: '2023-07-27T17:00:00',
      timeLeft: 0,
      daysLeft: null,
      hoursLeft: null,
      minutesLeft: null,
      secondsLeft: null,
    }
  },
  methods: {
    now() {
      return moment()
    },
    getTimeLeft() {
      return this.timeLeft = moment(this.endTime).diff(this.now(), 'seconds')
    },
  },
  mounted() {
    setInterval(() => {
      this.getTimeLeft()
    }, 1000)
  },
  watch: {
    timeLeft() {
      this.secondsLeft = this.timeLeft % 60
      this.minutesLeft = Math.floor(this.timeLeft / 60 % 60)
      this.hoursLeft = Math.floor(this.timeLeft / 3600 % 24)
      this.daysLeft = Math.floor(this.timeLeft / 86400)
    }
  }
}
</script>

<style>
#app {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%; 
  background: rgb(11,192,223);
  background: linear-gradient(90deg, rgba(11,192,223,1) 0%, rgba(252,221,89,1) 90%);
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  height: 100%;
  width: 100%;
}
.title {
  margin-bottom: 1rem;
  font-family: 'Emblema One', cursive;
  text-transform: uppercase;
  font-size: clamp(1.5rem, 0.656rem + 4.5vw, 6rem);
  color: red;
}
.timer {
  /* border: 1px solid olivedrab; */
  width: 90%;
  text-transform: uppercase;
}
.labels {
  /* border: 1px solid red; */
  display: flex;
  justify-content: space-evenly;
  /* align-items: ; */
  /* gap: 10px */
}
.labels > p {
  /* border: 1px solid white; */
  display: inline-block;
  text-align: center;
  width: 140px;
  margin: 0;
  padding: 5px 0;
  font-weight: 700;
  font-size: 48px;
}
.tiles {
  position: relative;
  /* border: 1px solid red; */
  display: flex;
  justify-content: space-evenly;
}
.tiles > .tile {
  /* border: 1px solid white; */
  display: flex;
  justify-content: center;
  align-items: center;
  width: 140px;
  aspect-ratio: 0.7446808510638298;
  height: 188px;
  font-size: clamp(1.5rem, 0.656rem + 4.5vw, 6rem);
  font-weight: 700;
  background-image: url('@/assets/tile.png');
  background-position: center;
  background-size: contain;
  transition: transform 1s;

}
.tile > span {
  transform: translateY(-10px);
}
.tile:nth-child(1) {
  color: #3b5899;
}
.tile:nth-child(4) {
  color: #ec2128;
}
.tile:nth-child(2) {
  color: #fddd59;
}
.bottom {
  /* border: 1px solid red; */
  height: 50%;
  max-height: 650px;
  min-width: 90%;
  overflow: hidden;
  display: flex;
  justify-content: space-around;
}
.image-left {
  max-height: 50%;
  transform: rotate(-30deg);
  align-self: center;
}
.image-right {
  max-height: 50%;
  align-self: center;
}
</style>
