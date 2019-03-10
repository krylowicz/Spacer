<template>
<!-- eslint-disable max-len -->
  <div class="outer-wrapper">
    <div class="inner-wrapper">
      <div class="photo">
        <img :src="photo">
      </div>
      <div class="description">
        <h2 class="title">{{ title }}</h2>
        <p class="description">{{ description }}</p>
      </div>
    </div>
    <div class="close" @click="$emit('closeModal')" />
  </div>
</template>

<script>
export default {
  name: 'Modal',
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
  data() {
    return {
      photo: null,
      title: null,
      description: null,
    };
  },
  mounted() {
    this.photo = this.item.links[0].href;
    this.title = this.item.data[0].title;
    this.description = this.item.data[0].description.substring(0, 200);
  },
};
</script>

<style lang="sass" scoped>
  @import '../sass/modal.sass'
</style>
