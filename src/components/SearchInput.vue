<template>
  <input id="search" name="search" :value="value" @input="handleChange" />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleChange(e) {
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="sass" scoped>
  @import '../sass/searchInput.sass'
</style>
