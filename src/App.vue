<template>
  <div>
     <PageHeader @search="search" />
     <PageMain :arr-films="arrFilms" :arr-series="arrSeries" />
  </div>
</template>

<script>
import axios from 'axios';
import PageHeader from '@/components/PageHeader.vue';
import PageMain from '@/components/PageMain.vue';

export default {
  name: 'App',
  components: {
    PageHeader,
    PageMain,
  },
  data() {
    return {
      arrSeries: null,
      arrFilms: null,
      urlApi: 'https://api.themoviedb.org/3',
      keyApi: '9776bd4da7d3b90c783bdbef13f8b137',
      languageApi: 'it-IT',
    };
  },
  methods: {
    search(search) {
      axios.get(`${this.urlApi}/search/movie`, {
        params: {
          api_key: this.keyApi,
          query: search,
          language: this.languageApi,
        },
      })
        .then((axiosResponse) => {
          console.log(axiosResponse);
          this.arrFilms = axiosResponse.data.results;
        });
      axios.get(`${this.urlApi}/search/tv`, {
        params: {
          api_key: this.keyApi,
          query: search,
          language: this.languageApi,
        },
      })
        .then((axiosResponse) => {
          console.log(axiosResponse);
          this.arrSeries = axiosResponse.data.results;
        });
    },
  },

};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";

   * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
</style>
