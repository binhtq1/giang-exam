<template>
  <div class="wrapper-app">
    <h1>Page Home</h1>
    <ul class="list-data" v-for="(list, index) in listData" :key="index" >
      <li>{{ list.data}}</li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      listData:[],
      errs: []
    }
  },

  mounted() {
    axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1/categories`)
        .then(res => {
          console.log('Result',res);
          this.listData = res.data
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
