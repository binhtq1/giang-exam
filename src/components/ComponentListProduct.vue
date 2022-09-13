<template>
  <div class="wrapper-list_product">
    <ComponentProductItem/>

    <!-- <h1>{{currentCatagory?.name}}</h1>
    <h2>{{currentCatagory?.slug}}</h2> -->

    <ul class="list-data" v-for="(product, index) in currentCatagory?.products" :key="index">
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
        currentCatagory: Object
    },
    components: { ComponentProductItem }
}
</script>

<style>

</style>