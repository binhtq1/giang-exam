<template>
  <div id="app">
    <div class="wrapper">
      <!--categories-->
      <div class="wrapper-left">
        <component-categories-list :categories="categories" :currentCategory="currentCategory"
          @get-product="getProducts" />
      </div>

      <!--content right-->
      <div class="wrapper-right">
        <div class="sort-filter">
          <component-filter-product />
        </div>
        <div class="list-product">
          <component-list-product :currentCategory="currentCategory" />
        </div>
        <div class="page-footer">
          <component-limit-page />
        </div>
      </div>
    </div>
  </div>


  <!-- <component-list-product :currentCatagory="currentCatagory" /> -->
</template>

<script>
import axios from 'axios'
import ComponentCategoriesList from './components/ComponentCategoriesList.vue'
import ComponentLimitPage from './components/ComponentLimitPage.vue'
import ComponentFilterProduct from './components/ComponentFilterProduct.vue'
import ComponentListProduct from './components/ComponentListProduct.vue'

// import ComponentListProduct from './components/ComponentListProduct.vue'
export default {
  name: 'App',
  components: {
    ComponentCategoriesList,
    ComponentLimitPage,
    ComponentFilterProduct,
    ComponentListProduct

  },
  data() {
    return {
      categories: [],
      products: [],
      // currentCategory: null,
      selectedCategory: null
    }
  },

  created() {
    axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories`)
      .then(res => {
        this.categories = res.data
        this.currentCategory = res.data[0]
        // console.log('currentCatagory', JSON.stringify(this.currentCatagory, undefined, 4));
      })
      .catch(err => {
        console.log(err);
      })
  },

  methods: {
    // Lấy SP theo categories
    getProducts() {
      axios
        .get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories/${this.selectedCategory}`)
        .then((response) => {
          this.products = response.data;
        })
        .catch((error) => {
          console.log(error);
        });
    },
  }
}
</script>

<style lang="scss" scoped>
@import '../src/sass/wrapper-app'
</style>
