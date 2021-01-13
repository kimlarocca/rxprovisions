<template>
  <div class="u-padding">
    <svg
        class="barcode"
        jsbarcode-format="CODE39"
        jsbarcode-value="123456789012"
        jsbarcode-textmargin="0"
        jsbarcode-fontoptions="bold"
    >
    </svg>
  </div>
</template>

<script>
import JsBarcode from 'jsbarcode'

export default {
  mounted () {
    JsBarcode('.barcode').init()
  }
}
</script>
