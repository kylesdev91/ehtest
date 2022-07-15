<template>
  <div class="cart-item-card">
    <div class="header">
      <h5>{{ product.name }}</h5>
      <h5>Qty: {{ product.quantity }}</h5>
      <h5>Total: ${{ item_cost.toFixed(2) }}</h5>
    </div>
  </div>
</template>

<script>
export default {
  props: ['product'],
  computed: {
    description() {
      return this.product.substring(0, 120);
    },
    item_cost() {
      return this.product.price * this.product.quantity;
    },
  },
};
</script>

<style lang="scss">
.cart-item-card {
  width: 100%;
  height: 50%;
  margin: 5%;
  background-color: white;
  box-shadow: 0 0 5px gray;
  border-radius: 5px;
  padding: 20px;
  text-align: right;
}
.header {
  display: flex;
  justify-content: space-around;
  text-align: right;
}
</style>
