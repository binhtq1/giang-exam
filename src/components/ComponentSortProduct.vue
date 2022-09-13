<template>
  <div class="wrapper-sort_product">
    <component-filter-product/>
    <component-sort-layout/>
  </div>
</template>

<script>
import ComponentFilterProduct from './ComponentFilterProduct.vue'
import ComponentSortLayout from './ComponentSortLayout.vue'
export default {
  components: {
     ComponentFilterProduct,
     ComponentSortLayout
    },
    name:'ComponentSortProduct',
    data() {
        return {
            
        }
    }
}
</script>

<style>

</style>