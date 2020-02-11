<template>
  <div id="app">
    <div v-if="!bShowScanner">
      <button v-on:click="showScanner">show scanner</button>
    </div>

    <div v-if="bShowScanner">
      <button v-on:click="hideScanner">hide scanner</button>
      <Quagga/>
    </div>
  </div>
</template>

<script>
import Quagga from './components/Quagga.vue'

export default {
  name: 'App',
  components: {
    Quagga
  },
  data () {
    return {
      bShowScanner: false
    }
  },
  methods: {
    showScanner(){
      this.bShowScanner = true;
    },
    hideScanner(){
      this.bShowScanner = false;
    }
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
