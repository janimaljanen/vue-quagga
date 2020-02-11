<template>
  <div style="text-align: left;">
    <div> format: {{ format }} | code: {{ code }} </div>
    <div class="popup-wrapper" v-if="popup">
      <img v-if="product = 'Pepsi MAX'" src="../assets/pepsimax.jpg"/>
      <img v-else-if="product = 'NOVELLE PLUS MULTI B+C'" src="../assets/novelle.jpg"/>
      <div>
        Löytyi tuote {{ product }}!
      </div>
      <button @click="hidePopup">Lisää ostoskoriin</button>
    </div>
    <div><v-quagga :onDetected="logIt" :readerSize="readerSize" :readerTypes="['ean_reader']"></v-quagga></div>
  </div>
</template>

<script>
import Vue from 'vue'
import VueQuagga from 'vue-quaggajs';

// register component 'v-quagga'
Vue.use(VueQuagga);

export default {
  name: 'VueBarcodeTest',
  data () {
    return {
      readerSize: {
        width: 640,
        height: 480
      },
      detecteds: [],
      code: "code_placeholder",
      format: "ean_placeholder",
      popup: false,
      product: ""
    }
  },
  methods: {
    logIt (data) {
      console.log('detected', data)
      this.code = data.codeResult.code
      this.format = data.codeResult.format
      if (this.code === "6413600015550") {
        this.popup = true
        this.product = "Pepsi MAX"
      } else if (this.code === "6413600004301" || this.code === "6413600017523") { // 6413600017523
        this.popup = true
        this.product = "NOVELLE PLUS MULTI B+C"
      }
    },
    showPopup(){
      this.popup = true;
    },
    hidePopup(){
      this.popup = false;
    }
  }
}
</script>

<style>
.popup-wrapper {
  position: absolute;
  z-index: 999;
  background-color: white;
  width: 100%;
  height: 100%;
  text-align: center;
  padding-top: 100px;
}
img {
  max-width: 250px;
  height: auto;
}
</style>