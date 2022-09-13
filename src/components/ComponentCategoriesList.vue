<template>
  <div class="wrapper-categories">
    <div class="button-categories">
      <button class="conditions">Clear conditions <br>(displayd in all categories)</button> <br>
      <button class="category">Category</button>
    </div>
    <div class="list-categories">
      <ul class="category-name" v-for="(list, index) in categories" :key="index">
        <li @click="handleRenderProduct">{{list.name}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComponentCategoriesList',
  props: {
    categories: Array
  },
  data() {
    return {
      productItem: []
    }
  },
  methods:{
    handleRenderProduct() {
      console.log("handleRenderProduct");
      this.productItem = this.products.id
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/categories-list'
</style>