<template>
  <main>
    <div v-if="dataMovies && dataMovies.results.length">
      <h2>
        Movies
      </h2>
      <div class="grid">
        <PageCard
          v-for="objMovie in dataMovies.results"
          :key="objMovie.id"
          :title="objMovie.title"
          :original-title="objMovie.original_title"
          :language="objMovie.original_language"
          :score="convertScore(objMovie.vote_average, originalMaxScore, newMaxScore)"
          :img-url="generateUrl(objMovie.poster_path)"
          :cast="objMovie.cast"
          class="card"
        />
      </div>
      <PaginatorComponent
        :page="dataMovies.page"
        :max-pages="dataMovies.total_pages"
        @changePage="$emit('changePage', {page: $event, type: 'movie'})"
      />
    </div>

    <div v-if="dataTv && dataTv.results.length">
      <h2>
        Serie TV
      </h2>
      <div class="grid">
        <PageCard
          v-for="objTv in dataTv.results"
          :key="objTv.id"
          :title="objTv.name"
          :original-title="objTv.original_name"
          :language="objTv.original_language"
          :score="convertScore(objTv.vote_average, originalMaxScore, newMaxScore)"
          :img-url="generateUrl(objTv.poster_path)"
          class="card"
        />
      </div>
      <PaginatorComponent
        :page="dataTv.page"
        :max-pages="dataTv.total_pages"
        @changePage="$emit('changePage', {page: $event, type: 'tv'})"
      />
    </div>
  </main>
</template>

<script>
import PageCard from '@/components/PageCard.vue';
import PaginatorComponent from '@/components/PaginatorComponent.vue';

export default {
  name: 'MainPage',
  components: {
    PageCard,
    PaginatorComponent,
  },
  props: {
    dataMovies: Object,
    dataTv: Object,
  },
  data() {
    return {
      baseImgUrl: 'https://image.tmdb.org/t/p/',
      imgSize: 'w342',
      originalMaxScore: 10,
      newMaxScore: 5,
    };
  },
  methods: {
    generateUrl(path) {
      if (path) {
        return this.baseImgUrl + this.imgSize + path;
      }
      return null;
    },
    convertScore(score, originalMaxScore, newMaxScore) {
      return {
        score: Math.ceil((score * newMaxScore) / originalMaxScore),
        maxScore: newMaxScore,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
  main {
    background-color: #525554;
    h2{
      color: red;
      padding: .3em 1em;
      font-size: 2em;
    }
  .grid {
    display: flex;
    flex-wrap: wrap;
  }
  .card {
    flex: 0 0 33%;
  }
}
</style>
