<template>
  <div class="wrapper-app">
    <h1>Page Home</h1>
    <ul class="list-data" v-for="(list, index) in listData" :key="index">
      <li>{{ list.name }}</li>
    </ul>

    <component-list-product :currentCatagory="currentCatagory" />
  </div>
</template>

<script>
import axios from 'axios'
import ComponentListProduct from './components/ComponentListProduct.vue'
export default {
  name: 'App',
  components: {
    ComponentListProduct

  },
  data() {
    return {
      listData: [],
      errs: [],
      currentCatagory: null,
    }
  },

  created() {
    axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories`)
      .then(res => {
        // console.log('Result', res);
        this.listData = res.data
        this.currentCatagory = res.data[1]
        // console.log('currentCatagory', JSON.stringify(this.currentCatagory, undefined, 4));
      })
      .catch(err => {
        console.log(err);
      })
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.wrapper-app {
  width: 100vw;
  height: auto;
  border: 1px solid #ccc;
}
</style>
