<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Quagga/>
  </div>
</template>

<script>
import Quagga from './components/Quagga.vue'

export default {
  name: 'App',
  components: {
    Quagga
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
