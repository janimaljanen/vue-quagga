<template>
  <div style="text-align: left;">
    <div> format: {{ format }} | code: {{ code }} </div>
    <div class="popup-wrapper" v-if="popup">
      <img v-if="product === 'Pepsi MAX'" src="../assets/pepsimax.jpg"/>
      <img v-if="product === 'NOVELLE PLUS MULTI B+C'" src="../assets/novelle.jpg"/>
      <img v-if="product === 'ED GREENFRUIT NO SUGAR'" src="../assets/ed_green.jpg"/>
      <img v-if="product === 'HARTWALL ORIGINAL LONG SHOT 15,5%'" src="../assets/long_shot.jpg"/>
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
      switch  (this.code) {
        case "6413600015550":
          this.product = "Pepsi MAX"
          this.popup = true
          break;
        case "6413600017523":
          this.product = "NOVELLE PLUS MULTI B+C"
          this.popup = true
          break;
        case "6413600156864":
          this.product = "ED GREENFRUIT NO SUGAR"
          this.popup = true
          break;
        case "6413600195986":
          this.product = "HARTWALL ORIGINAL LONG SHOT 15,5%"
          this.popup = true
          break;
        default:
          // code block
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