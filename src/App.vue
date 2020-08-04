<template>
  <div id="app">
    <input type="text" v-model="barcodeValue">

    <h1>
      {{ textboxFillType }}
    </h1>
  </div>
</template>

<script>
import onscan from 'onscan.js'

export default {
  name: 'App',
  data() {
    return {
      barcodeValue: '',
      textboxFillType: ''
    }
  },

  mounted() {
    onscan.attachTo(document, {
      onScan: (barcode) => {
          this.barcodeValue = barcode;
          this.textboxFillType = 'Textbox fill using barcode sccaner.'
      },

      onKeyProcess: () => {
        this.textboxFillType = 'Textbox fill using keyboard.'
      }
    });
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
