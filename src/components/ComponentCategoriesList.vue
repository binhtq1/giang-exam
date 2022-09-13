<template>
  <div class="wrapper-categories">
    <div class="button-categories">
      <button class="conditions">Clear conditions <br>(displayd in all categories)</button> <br>
      <button class="category">Category</button>
    </div>
    <div class="list-categories">
      <ul class="category-name" v-for="(category, index) in categories" :key="index">
        <li @click="setCurrentCategory(category)">{{category.name}}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ComponentCategoriesList',
  props: {
    categories: Array,
    // currentCategory: Object
  },
  data() {
    return {
    }
  },
  methods: {
    setCurrentCategory(category) {
      console.log('get product click');
      this.$emit('get-product', category)
      // this.currentCategory = category
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/categories-list'
</style>