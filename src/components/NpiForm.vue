<template>
  <div class="npi-form">
    <div class="order-form l-container">
      <h2>Order Your Prescription Pad Now!</h2>
      <div class="input-group">
        <label
            for="inline-input"
            class="hide-ally-element"
        >NPI Number</label>
        <input
            id="inline-input"
            class="input-group-field"
            type="number"
            placeholder="Enter Your NPI Number"
            v-model="id"
        >
        <div class="input-group-button">
          <input
              type="submit"
              class="button"
              value="Go"
              @click="goToOrderPage"
          >
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import router from "@/router";

export default {
  name: 'NpiForm',
  data () {
    return {
      id: {
        type: Number,
        default: null
      }
    }
  },
  methods: {
    goToOrderPage () {
      router.push({ name: 'Order', query: { ID: this.id } })
    }
  }
}
</script>

<style lang="scss">
.npi-form {
  background: url("/images/home-hero2.jpg") no-repeat;
  background-size: cover;
  padding: 140px 0;
  text-align: center;
  color: var(--color-white);

  h2 {
    text-shadow: 0 0 20px var(--color-black);
    margin-bottom: var(--space-4);
  }

  .input-group {
    max-width: 650px;
    margin: auto;
  }
}
</style>
