<template>
  <div class="cart-item-card">
    <h5>Cart Total: ${{ cart_total.toFixed(2) }}</h5>
    <button class="submit">Submit</button>
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
  font-size: 25px;
  text-align: left;

  .submit {
    background-color: green;
    font-weight: bold;
    padding: 20px;
    width: 15%;
    color: white;
    font-size: 25px;
    width: 200px;
    margin-left: 10px;
    height: 100%;
    text-align: center;
  }
}
</style>
