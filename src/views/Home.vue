<template>
  <div class="home">
    <div class="product-cards-container">
      <ProductDescriptionDrawer
        :product="product"
        :active="active.product_drawer"
        v-on:close-product-drawer="closeDrawer()"
      />
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
import items from "../data/items.js";
import ProductSummaryCard from "../components/products/ProductSummaryCard.vue";
import ProductDescriptionDrawer from "../components/products/ProductDescriptionDrawer.vue";

export default {
  name: "Home",
  components: {
    ProductSummaryCard,
    ProductDescriptionDrawer,
  },
  methods: {
    viewProduct(product) {
      this.product = product;
      this.active.product_drawer = true;
    },
    closeDrawer() {
      this.active.product_drawer = false;
    },
  },
  data() {
    return {
      product: null,
      items: items,
      active: {
        product_drawer: false,
      },
    };
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
