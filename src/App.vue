<template>
  <div>
    <PageHeader @queryChange="search" />
    <PageMain
      :data-movies="dataMovies"
      :data-tv="dataTv"
      @changePage="changePage"
    />
  </div>
</template>

<script>
import axios from 'axios';
import Vue from 'vue';
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
      baseApiUrl: 'https://api.themoviedb.org/3',
      apiKey: '9776bd4da7d3b90c783bdbef13f8b137',
      resultsLanguage: 'it-IT',
      dataMovies: null,
      dataTv: null,
      queryString: '',
    };
  },
  methods: {
    search(queryString) {
      this.queryString = queryString;
      axios.get(`${this.baseApiUrl}/search/movie`, {
        params: {
          api_key: this.apiKey,
          language: this.resultsLanguage,
          query: queryString,
        },
      })
        .then((responseAxios) => {
          this.dataMovies = responseAxios.data;
          responseAxios.data.results.forEach((objMovie) => {
            axios.get(`${this.baseApiUrl}/movie/${objMovie.id}/credits`, {
              params: {
                api_key: this.apiKey,
              },
            })
              .then((axiosResponse) => {
                const movie = objMovie;
                Vue.set(movie, 'cast', axiosResponse.data.cast.slice(0, 5).map((objActor) => objActor.name));
              });
          });
        });
      axios.get(`${this.baseApiUrl}/search/tv`, {
        params: {
          api_key: this.apiKey,
          language: this.resultsLanguage,
          query: queryString,
        },
      })
        .then((responseAxios) => {
          this.dataTv = responseAxios.data;
        });
    },
    changePage(info) {
      switch (info.type) {
        case 'movie':
          axios.get(`${this.baseApiUrl}/search/movie`, {
            params: {
              api_key: this.apiKey,
              language: this.resultsLanguage,
              query: this.queryString,
              page: info.page,
            },
          })
            .then((responseAxios) => {
              this.dataMovies = responseAxios.data;
            });
          break;
        case 'tv':
          axios.get(`${this.baseApiUrl}/search/tv`, {
            params: {
              api_key: this.apiKey,
              language: this.resultsLanguage,
              query: this.queryString,
              page: info.page,
            },
          })
            .then((responseAxios) => {
              this.dataTv = responseAxios.data;
            });
          break;
        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
