<template>
  <div id="products" class="box">
    <div class="products-header has-text-centered">
      <i class="fa fa-2x fa-user-circle"></i>
    </div>
    <div class="product-list">
      <div class="product-list--item" v-for="productItem in productItems" :key="productItem.id">
        <ProductListItem :productItem="productItem" />
      </div>
    </div>
    <div class="product-count has-text right">
      <span class="has-text-weight-bold"># of products: 4</span>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import ProductListItem from './ProductListItem.vue';

export default {
  components: { ProductListItem },
  name: "ProductList",
  created() {
    this.$store.dispatch("getProductItems");
  },
  computed: mapGetters({
    productItems: "productItems",
  }),
};
</script>

<style scoped>
.products--header {
  border-bottom: 1px solid #e8e8e8;
  padding-bottom: 15px;
}

.product-list {
  padding-top: 10px;
}

.product-list--item {
  padding: 10px 0;
}
</style>