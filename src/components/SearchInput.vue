<template>
  <div class="search-wrapper">
   <div class="search">
      <input id="search" name="search" v-model="searchValue" @input="handleInput" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
}
</script>

<style lang="sass" scoped>
  @import '../sass/searchInput.sass'
</style>
