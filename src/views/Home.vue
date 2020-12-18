<template>
  <div class="home l-container">
    <div class="l-grid l-grid--2up l-grid--middle">
      <h1>Completely Novel Gene Therapies</h1>
      <p>GeneLeap Bioteach is a global gene therapy company in the Luye Lifesciences portfolio of companies, a leader in China and a new entrant in the US. Our goal is to deliver a best-in-class portfolio of completely novel gene therapies.</p>
    </div>
    <v-spacer size="quin" />
    <div class="home-hero">
      <div class="home-hero-circle" />
      <img
          src="/images/home-hero.jpg"
          alt="GeneLeap Bioteach, a global gene therapy company"
      />
    </div>
  </div>
</template>

<script>
import VSpacer from 'vue-evolve/src/components/VSpacer'

export default {
  name: 'Home',
  components: {
    VSpacer
  }
}
</script>

<style lang="scss">
@import "src/assets/settings";
.home {
  position: relative;
  &::after {
    position: absolute;
    top: 0;
    right: -320px;
    content: '';
    height: 300px;
    width: 300px;
    border-radius: 50%;
    background: var(--color-quaternary);
    background: linear-gradient(180deg, var(--color-white) 0%, var(--color-tertiary) 50%, var(--color-tertiary) 100%);

  }
}
.home .home-hero {
  width: 100%;
}

.home .home-hero-circle {
  position: relative;
  height: 100px;
  overflow: hidden;

  &::before {
    content: '';
    position: absolute;
    top: 0;
    left: 32px;
    height: 300px;
    width: 300px;
    border-radius: 50%;
    background: var(--color-primary);
    background: linear-gradient(90deg, var(--color-quinary) 0%, var(--color-primary) 100%);
    @media all and (min-width: $medium) {
      left: 100px;
      height: 400px;
      width: 400px;
    }
  }
}
</style>
