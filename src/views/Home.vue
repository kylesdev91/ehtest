<template>
  <div class="home">
    <div class="product-cards-container">
      <ProductSummaryCard
        v-for="product in items"
        :key="product.id"
        :product="product"
        v-on:view-product="viewProduct($event)"
      />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import items from '../data/items.js';
import ProductSummaryCard from '../components/products/ProductSummaryCard.vue';

export default {
  name: 'Home',
  components: {
    ProductSummaryCard,
  },
  data() {
    return {
      items: items,
      product: null,
    };
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      console.log(this.product);
    },
  },
};
</script>

<style lang="scss">
.product-cards-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
