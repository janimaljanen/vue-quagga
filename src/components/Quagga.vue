<template>
  <div style="text-align: left;">
    <div> {{ code }} </div>
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
      code: "placeholder"
    }
  },
  methods: {
    logIt (data) {
      console.log('detected', data)
      this.code = data.codeResult.code
    }

  }
}
</script>