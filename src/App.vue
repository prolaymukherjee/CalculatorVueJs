<template>
  <div id="app">
    <Calculator msg="Calculator"/>
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue'

export default {
  name: 'app',
  components: {
      Calculator
  }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
    background-image: url("./assets/bg.jpg");
    background-repeat: no-repeat;
    background-size: 850px 800px;
    background-position: center;
}
</style>
