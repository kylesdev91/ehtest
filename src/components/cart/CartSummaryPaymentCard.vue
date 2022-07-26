<template>
  <div class="cart-item-card">
    <div style="text-align: center">
      <h5>Cart Total: ${{ cart_total.toFixed(0) }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  name: 'CartSummaryPaymentCard',
  data() {
    return {
      userTotal: console.log(this.$store.getters.cartTotal),
    };
  },
  computed: {
    cart_total() {
      return this.$store.getters.cartTotal;
    },
  },
  props: {
    getTotal: Function,
  },
};
</script>

<style lang="scss">
.cart-item-card {
  /* height: 60px; */
  font-size: 25px;
  margin-bottom: 40px;
  /* margin-top: 40px; */
  /* position: relative; */
  /* text-align: left; */

  .submit {
    background-color: green;
    /* font-weight: bold; */
    padding: 10px;
    /* width: 15%; */
    color: white;
    font-size: 20px;
    /* width: 200px; */
    /* margin-left: 10px; */
    /* height: 100%; */

    /* position: relative; */
    /* margin: auto; */
  }
}
</style>
