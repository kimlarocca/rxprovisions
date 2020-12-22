<template>
  <div class="home">
    <div class="home-hero">
      <div class="l-container l-grid l-grid--3x2 l-grid--1up--small l-grid--large-gutters">
        <div class="home-hero-left">
          <h1>Providing secure prescription solutions to the healthcare industry since 1997</h1>
          <p>New Jersey’s first approved vendor for Security Rx forms, RX PROvisions provides safe and secure healthcare forms to doctors for use and distribution to their patients, and offer significant discounts to our re-sellers.</p>
          <v-button href="/order">Get Started</v-button>
        </div>
        <div class="home-hero-right">
          <picture>
            <source
                srcset="/images/home-hero.webp"
                type="image/webp"
            >
            <source
                srcset="/images/home-hero.jpg"
                type="image/jpeg"
            >
            <img
                src="/images/home-hero.jpg"
                alt="RX PROvisions"
            >
          </picture>
        </div>
      </div>
    </div>
    <div class="home-hero-mobile">
      <picture>
        <source
            srcset="/images/home-hero-mobile.webp"
            type="image/webp"
        >
        <source
            srcset="/images/home-hero-mobile.jpg"
            type="image/jpeg"
        >
        <img
            src="/images/home-hero-mobile.jpg"
            alt="RX PROvisions"
        >
      </picture>
    </div>
    <v-spacer size="quad" />
    <div class="home-cards l-container l-grid l-grid--3up l-grid--large-gutters">
      <div>
        <card
            icon="fas fa-edit"
            subtitle="customizable"
            description="We allow our customers to customize their practice information on portrait or landscape Rx Forms"
        />
      </div>
      <div>
        <card
            icon="fas fa-user-tie"
            subtitle="professional"
            description="Our number one goal is to provide professional and personalized service at the national, state, and local levels."
        />
      </div>
      <div>
        <card
            icon="fas fa-lock"
            subtitle="secure"
            description="We offer innovative, trustworthy products that comply with State and DOJ guidelines and are completely secure."
        />
      </div>
    </div>
    <v-spacer size="quin" />
    <npi-form />
  </div>
</template>

<script>
import NpiForm from '../components/NpiForm'
import VButton from 'vue-evolve/src/components/VButton'
import VSpacer from 'vue-evolve/src/components/VSpacer'
import Card from 'vue-evolve/src/components/Card'

export default {
  name: 'Home',
  components: {
    NpiForm,
    VButton,
    VSpacer,
    Card
  }
}
</script>

<style lang="scss">
@import "src/assets/settings";

.home-hero {
  background: var(--color-primary);
  padding: var(--space-4) 0;
  color: var(--color-white);

  @media all and (min-width: $large) {
    background: linear-gradient(var(--color-primary) 80%, var(--color-white) 20%);
  }

  h1 {
    margin-bottom: var(--space-4);
    max-width: 600px;
  }

  p {
    margin-bottom: var(--space-4);
  }

  .home-hero-left {
    padding-bottom: var(--space-6);
  }

  .home-hero-right {
    display: none;
    @media all and (min-width: $medium) {
      display: block;
    }
  }
}

.home-hero-mobile {
  @media all and (min-width: $medium) {
    display: none;
  }
}

.home-cards {
  text-align: center;

  .card {
    box-shadow: 0px 0px 30px 0px rgba(0, 0, 0, 0.15);

    .subtitle {
      text-transform: uppercase;
    }
  }

  i {
    font-size: 2rem;
    color: var(--color-secondary);
  }
}
</style>
