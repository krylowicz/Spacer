<template>
<!-- eslint-disable max-len -->
  <input id="search" name="search" placeholder=" e.g. moon" :value="value" @input="handleChange" :class="{ dark }" />
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
    dark: {
      type: Boolean,
      default: false,
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
