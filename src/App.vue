<template>
  <div>
    <the-header />
    <router-view />
    <the-footer />
  </div>
</template>

<script>
import TheHeader from '../src/components/TheHeader'
import TheFooter from '../src/components/TheFooter'

export default {
  name: 'RxProvisions',
  components: {
    TheFooter,
    TheHeader
  }
}
</script>
