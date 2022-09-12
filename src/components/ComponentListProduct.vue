<template>
  <div class="wrapper-list_product">
    <h1>ComponentProductList</h1>
    <h1>{{currentCatagory?.name}}</h1>
    <h2>{{currentCatagory?.slug}}</h2>

    <ul class="list-data" v-for="(product, index) in currentCatagory?.products" :key="index">
      <li>{{ product.name}}</li>
      <li>{{ product.price}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ComponentProductList',
  data() {
    return {

    }
  },
  props: {
    currentCatagory: Object
  }
}
</script>

<style>

</style>