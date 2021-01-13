<template>
  <div class="u-padding">
    <input v-model="code">
    <svg
        class="barcode"
        jsbarcode-format="CODE39"
        :jsbarcode-value="code"
        jsbarcode-textmargin="0"
        jsbarcode-fontoptions="bold"
    >
    </svg>
  </div>
</template>

<script>
import JsBarcode from 'jsbarcode'

export default {
  data () {
    return {
      code: 123456789
    }
  },
  mounted () {
    JsBarcode('.barcode').init()
  },
  watch: {
    code () {
      JsBarcode('.barcode').init()
    }
  }
}
</script>
