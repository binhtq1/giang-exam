<template>
  <div class="wrapper-categories">
    <div class="button-categories">
      <div class="button-control">
        <button class="conditions">Clear conditions <br>(displayd in all categories)</button> <br>
        <button class="category">Category aaaa</button>
      </div>


      <!--SORT PRODUCT-->
      <div class="filter-product">
        <select @change="sortActivePrice">
          <option value="0">Default</option>
          <option>Price</option>
        </select>

        <button @click="isSortListProduct = false"><i class="fas fa-th-large"></i></button>
        <button @click="isSortListProduct = true"><i class="fas fa-bars"></i></button>
      </div>
    </div>

    <div class="category-product">
      <!--RENDER LIST CATEGORY-->
      <div class="list-categories">
        <ul class="category-name" v-for="(category, index) in categories" :key="index">
          <li @click="getProductCategory(category)"><strong>{{ category.name }}</strong></li>
        </ul>
      </div>

      <!--RENDER PRODUCT THEO CATEGORY-->
      <div class="list-product" :class="{ activeproduct: isSortListProduct, loader: isLoading }">
        <div class="hieuung3" v-if="isLoading">
          <h2>Loading...</h2>
          <span class="rect1"></span>
          <span class="rect2"></span>
          <span class="rect3"></span>
          <span class="rect4"></span>
          <span class="rect5"></span>
        </div>
        <ul class="item-product" v-for="product in products" :key="product.id">
          <li><img :src="product.thumbnail" alt="IMAGE" /></li>
          <li class="name-product"> {{ product.name }}</li>
          <li class="price-product"> <strong>Price:</strong> <strong class="price-hightlight">{{ product.price
            + " " + "$" }}</strong></li>
          <li class="stock-product"><strong>Stock: </strong>{{ product.inStock }}</li>
          <li class="description-product"> <strong>Description:</strong> {{ product.description }}</li>
        </ul>
      </div>
    </div>

  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'ComponentCategoriesList',
  props: {
    categories: Array,
  },
  data() {
    return {
      products: [],
      sortPrice: null,
      selectedCategory: null,
      isSortListProduct: false,
      isLoading: false
    }
  },

  methods: {
    // LẤY THÔNG TIN SẢN PHẨM THEO CLICK CATEGORY
    getProducts() {
      this.isLoading = true
      axios
        .get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories/${this.selectedCategory}`)
        .then((res) => {
          this.products = res.data.products
          console.log('------------->', res.data.products);
        })
        .catch((error) => {
          console.log(error);
        })
        .finally(() => {
          this.isLoading = false
        })
    },
    getProductCategory(category) {
      this.selectedCategory = category.id;
      this.getProducts()
    },


    // SORT THEO PRICE
    sortPriceProduct() {
      this.isLoading = true
      axios
        .get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories/${this.selectedCategory}/products?sortBy=price&order=asc`)
        .then(res => {
          this.products = res.data
          console.log("PRODUCT", res.data);
        })
        .catch(err => {
          console.log(err);
        })
        .finally(() => {
          this.isLoading = false
        })
    },
    sortActivePrice(category) {
      this.sortPrice = category.id
      this.sortPriceProduct()
    }
  },

}
</script>

<style lang="scss" scoped>
@import '../sass/categories-list';
@import '../sass/list-product';
@import '../sass/activeproduct';
@import '../sass/filterproduct';
@import '../sass/loading';
</style>










