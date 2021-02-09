<template>
  <div class="footer-container">
    <v-footer company-name="RxPROvisions, Inc.">
      <template v-slot:logo>
        <v-logo />
      </template>
      <template v-slot:blurb>
        <p>4 Beaver Brook Road, Suite 127 Lincoln Park, NJ 07035</p>
        <p>973-305-8105</p>
        <p><a href="mailto:mail@RxPROvisions.com">mail @ RxPROvisions.com</a></p>
      </template>
    </v-footer>
  </div>
</template>

<script>
import VFooter from 'vue-evolve/src/components/TheFooter'
import VLogo from '../components/VLogo'

export default {
  name: 'TheFooter',
  components: {
    VFooter,
    VLogo
  }
}
</script>

<style lang="scss">
.footer {
  font-size: var(--font-size-4);
}

.footer .secondary-navigation-item {
  text-transform: uppercase;
  margin: var(--space-2);
}

.footer a,
.footer a:visited,
.footer a:active {
  padding-bottom: var(--space-2);
  border-bottom: solid 1px var(--color-white);
}

.footer .logo a {
  border: none;
}
</style>
