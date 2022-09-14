<template>
  <div class="wrapper-list_product">
    <ComponentProductItem />

    <!-- <ul class="list-data" v-for="(product, index) in currentCategory?.products" :key="index">
      <li>{{ product.thumbnail }}</li>
      <li>{{ product.name }}</li>
      <li>{{ product.price }}</li>
      <li>{{ product.description }}</li>
    </ul> -->

    <!--example-->
    <div>
      <ul class="list-data" v-for="product in products" :key="product.id">
        <li> PRICE: {{ product.price }}</li>
        <li> NAME: {{ product.name }}</li>
        <li> INSTOCK: {{ product.inStock }}</li>
      </ul>
    </div>

  </div>
</template>

<script>
import ComponentProductItem from './ComponentProductItem.vue';
export default {
  name: "ComponentProductList",
  data() {
    return {};
  },
  props: {
    products: Array,
    // selectedCategory: null
  },
  components: { ComponentProductItem },

}
</script>

<style>

</style>