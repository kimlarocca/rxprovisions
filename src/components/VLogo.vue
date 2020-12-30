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
.logo {
  font-size: 1.5rem;
  font-weight: bold;

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
