<template>

  <div>
    <button :class="{ active: isActive}" @click="pageHomeClick(category)">1</button>
    <button :class="{ active: isActive}" @click="page2Click(category)">2</button>
  </div>

</template>

<script>
export default {
  name: 'ComponentPagination',
  data() {
    return {
      isActive: false
    }
  },
  methods: {
    pageHomeClick(category) {
      this.$emit('page-1', category)
    },
    page2Click(category) {
      this.$emit('page-2', category)
    },
  }
}
</script>

<style lang="scss" scoped>
@import '../sass/pagination';
@import '../sass/active';
</style>