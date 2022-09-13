<template>
  <div class="wrapper-list_product">
    <ComponentProductItem />

    <ul class="list-data" v-for="(product, index) in currentCategory?.products" :key="index">
      <li>{{ product.thumbnail }}</li>
      <li>{{ product.name }}</li>
      <li>{{ product.price }}</li>
      <li>{{ product.description }}</li>
    </ul>

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
    currentCategory: Object
  },
  components: { ComponentProductItem },

}
</script>

<style>

</style>