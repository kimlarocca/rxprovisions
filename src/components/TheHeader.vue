<template>
  <div class="header-container">
    <v-header
        layout="right"
        responsive="true"
    >
      <template v-slot:logo>
        <v-logo />
      </template>
      <template v-slot:button>
        <router-link to="order">
          <v-button>
            Order Online
          </v-button>
        </router-link>
      </template>
    </v-header>
  </div>
</template>

<script>
import VButton from 'vue-evolve/src/components/VButton'
import VHeader from 'vue-evolve/src/components/VHeader'
import VLogo from '../components/VLogo'

export default {
  name: 'TheHeader',
  components: {
    VButton,
    VHeader,
    VLogo
  }
}
</script>

<style lang="scss">
.header-container {
  background: var(--color-primary);
  padding: var(--space-6) 0;
}


.header .secondary-navigation-item {
  text-transform: uppercase;
  font-size: var(--font-size-5);
  font-weight: 600;
}

.header .button,
.header .button:visited,
.header .button:active {
  background: var(--color-white);
  border-color: var(--color-white);
  color: var(--color-primary);
  font-size: var(--font-size-5);
  font-weight: 600;

  &:hover {
    background: var(--color-primary);
    border-color: var(--color-white);
    color: var(--color-white);
  }
}
</style>
