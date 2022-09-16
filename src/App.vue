<template>
  <div id="app">
    <div class="wrapper">

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
    }
  },

  // LẤY TẤT CẢ DỮ LIỆU
  created() {
    axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories`)
      .then(res => {
        console.log(res);
        this.categories = res.data
        console.log("CREATED", res.data);
      })
      .catch(err => {
        console.log(err);
      })
  },
}
</script>

<style lang="scss" scoped>
@import '../src/sass/wrapper-app'
</style>