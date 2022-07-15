<template>
  <div class="card">
    <h3>{{ product.name }}</h3>
    <h5 class="price">Price: ${{ product.price.toFixed(0) }} / lb</h5>
    <button class="view-product-button" @click="$emit('view-product', product)">
      View Product
    </button>
    <button v-on:click="addItemToCart(product)">Add to cart</button>
    <img :src="product.image" />
  </div>
</template>

<script>
export default {
  props: ['product'],
  computed: {
    description() {
      return this.product.substring(0, 150);
    },
  },
};
</script>

<style lang="scss">
.card {
  width: 80%;
  margin: 10%;
  padding: 10px;
  border-radius: 5px;
  background-color: white;
  box-shadow: 0 0 5px gray;

  h5.price {
    color: gray;
    font-weight: bold;
  }

  p.description {
    font-size: 0.85rem;
  }

  p.text-muted {
    color: gray;
  }

  button.view-product-button {
    padding: 10px;
    background-color: rgb(79, 160, 187);
    border: none;
    color: white;
    font-weight: bold;
    font-size: 1.15rem;
    border-radius: 5px;
    cursor: pointer;
    font-weight: bold;
    background-color: teal;
    margin-right: 30px;
    color: white;
    font-size: 20px;
  }
}

@media (min-width: 500px) {
  .card {
    width: 350px;
    margin: 10px;
  }
}
</style>
