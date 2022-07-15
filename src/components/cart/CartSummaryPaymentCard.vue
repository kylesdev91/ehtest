<template>
  <div class="cart-item-card">
    <h3>Cart Total: ${{ cart_total.toFixed(2) }}</h3>
  </div>
</template>

<script>
export default {
  computed: {
    cart_total() {
      return this.$store.getters.cartTotal;
    },
  },
};
</script>

<style lang="scss">
.cart-item-card {
  height: 60px;
  font-size: 20px;
  text-align: inherit;
}
</style>
