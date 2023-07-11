<template>
  <div class="hello">
    <h1 class="title">Wielkie odliczanie</h1>
    <div class="bottom">
      <image class="image-left" src="../assets/logoR.png" alt="Rummikube Logo R"/>
      <image class="image-center" alt="event banner" />
      <image class="image-right" src="../assets/face.png" alt="rummi-logo-face"/>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .hello {
    position: absolute;
    top: 0;
    left: 0;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: 100%;
    background: rgb(11,192,223);
    background: linear-gradient(90deg, rgba(11,192,223,1) 0%, rgba(252,221,89,1) 100%);
  }
  .title {
    font-family: 'Emblema One', cursive;
    text-transform: uppercase;
    font-size: 48px;
    color: red;
  }
  .time {
    width: max-content;
  }
  .timer__label {
    display: flex;
    justify-content: space-evenly;
  }
  
</style>
