<template>
  <div class="logo">
    <router-link to="/"><i class="fas fa-prescription"></i>PROvisions, Inc.</router-link>
  </div>
</template>

<script>
export default {
  name: 'VLogo'
}
</script>

<style lang="scss">
@import "src/assets/settings";

.logo {
  font-size: 1rem;
  font-weight: bold;

  @media all and (min-width: $small) {
    font-size: 1.4rem;
  }

  @media all and (min-width: $medium) {
    font-size: 1.5rem;
  }

  i {
    font-size: 2rem;
  }

  a,
  a:visited,
  a:active {
    color: var(--color-white);
    transition: var(--transition);

    &:hover {
      color: var(--color-white);
      opacity: var(--opacity-on-hover);
    }
  }
}
</style>
