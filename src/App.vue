<template>
  <div id="app">
    <div class="wrapper" :class="{ loader: isLoading}">
      <div class="hieuung3" v-if="isLoading">
        <h2>Loading...</h2>
        <span class="rect1"></span>
        <span class="rect2"></span>
        <span class="rect3"></span>
        <span class="rect4"></span>
        <span class="rect5"></span>
      </div>

      <!--categories-->
      <div class="wrapper-content">
        <component-categories-list :categories="categories" />
      </div>

    </div>
  </div>
</template>

<script>
import axios from 'axios'
import ComponentCategoriesList from './components/ComponentCategoriesList.vue'

export default {
  name: 'App',
  components: {
    ComponentCategoriesList,
  },
  data() {
    return {
      categories: [],
      isLoading: false
    }
  },

  // LẤY TẤT CẢ DỮ LIỆU
  created() {
    this.getDataApi();
  },

  methods: {
    getDataApi() {
      this.isLoading = true;
      axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories`)
        .then(res => {
          console.log(res);
          this.categories = res.data
          console.log("CREATED", res.data);
        })
        .catch(err => {
          console.log(err);
        })
        .finally(() => {
          this.isLoading = false;
        })
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../src/sass/wrapper-app';
@import '../src/sass/loading';
</style>