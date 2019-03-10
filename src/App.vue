<template>
  <div class="wrapper">
    <HeroImage />
    <Claim />
    <SearchInput v-model="searchValue" @input="handleInput" />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'App',
  components: {
    Claim,
    SearchInput,
    HeroImage,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function() {
      console.log(this.searchValue);
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="sass">
  @import 'sass/search.sass'
  @import url('https://fonts.googleapis.com/css?family=Montserrat:300,400,600,800')

  *
    box-sizing: border-box
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;

  body
    font-family: 'Montserrat', sans-serif
    padding: 0
    margin: 0
</style>
