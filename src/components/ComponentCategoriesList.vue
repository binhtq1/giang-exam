<template>
  <div class="wrapper-categories">
    <div class="button-categories">
      <div class="button-control">
        <button class="conditions">Clear conditions <br>(displayd in all categories)</button> <br>
        <button class="category">Category</button>
      </div>
      

      <!--SORT PRODUCT-->
      <div class="filter-product">
        <select @change="sortProduct">
          <option value="0" >Default</option>
          <option>Name</option>
          <option>Price</option>
        </select>
      </div>
    </div>

    <div class="category-product">
      <!--RENDER LIST CATEGORY-->
      <div class="list-categories">
        <ul class="category-name" v-for="(category, index) in categories" :key="index">
          <li @click="getProductCategory(category)"><strong>{{category.name}}</strong></li>
        </ul>
      </div>

      <!--RENDER PRODUCT THEO CATEGORY-->
      <div class="list-product">
        <ul class="item-product" v-for="product in products" :key="product.id">
          <li><img :src="product.thumbnail" alt="IMAGE" /></li>
          <li class="name-product"> {{ product.name }}</li>
          <li class="price-product"> <strong>Price:</strong> <strong class="price-hightlight">{{ product.price +" "+"$"}}</strong></li>
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
      sortName: null,
      selectedCategory: null
    }
  },

  methods: {
    // LẤY THÔNG TIN SẢN PHẨM THEO CLICK CATEGORY
    getProducts() {
      axios
        .get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories/${this.selectedCategory}`)
        .then((res) => {
          this.products = res.data.products
        })
        .catch((error) => {
          console.log(error);
        });
    },

    // HÀM XỬ LÝ KHI CLICK VÀO TỪNG TÊN CATEGORY
    getProductCategory(category) {
      this.selectedCategory = category.id;
      this.getProducts()
    },

    // CHANGE
    sortProduct() {
      console.log('CHANGE');
      axios
        .get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories?sortBy=name&order=desc`)
        .then(res => {
          this.products = res.data.products
          console.log("PRODUCT", res.data.products);
        })
        .catch(err => {
          console.log(err);
        })
    }
  },

}
</script>

<style lang="scss" scoped>
@import '../sass/categories-list'
</style>










