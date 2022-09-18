<template>
  <div>
    <button @click="pageHomeClick">1</button>
    <button @click="page2Click">2</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'ComponentPagination',
  data() {
    return {
      products: []
    }
  },
  methods: {
    pageHomeClick() {
      console.log('click 1');
      axios.get(`https://631ed88058a1c0fe9f594c50.mockapi.io/api/v1//categories?page=1&limit=3`)
        .then(res => {
          this.products = res.data
          console.log('-------------PAGE', res.data);
        })
        .catch(err => {
          console.log(err);
        })
    },
    page2Click() {
      console.log('click 2');
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/pagination'
</style>