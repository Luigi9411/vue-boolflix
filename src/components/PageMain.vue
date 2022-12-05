<template>
  <div>
     <h2 v-if="arrFilms.length">
        Film
     </h2>
     <PageCard
      v-for="objFilm in arrFilms"
      :key="objFilm.id"
      :title="objFilm.title"
      :original-title="objFilm.original_title "
      :language="objFilm.original_language"
      :score="convertScore(objFilm.vote_average)"
      :imgUrl="generateUrl(objFilm.poster_path)"
      />
      <h2 v-if="arrSeries.length">
        Serie tv
    </h2>
     <PageCard
      v-for="objSeries in arrSeries"
      :key="objSeries.id"
      :title="objSeries.name"
      :original-title="objSeries.original_name "
      :language="objSeries.original_language"
      :score="convertScore(objSeries.vote_average)"
      :imgUrl="generateUrl(objSeries.poster_path)"
      />
  </div>
</template>

<script>
import PageCard from '@/components/PageCard.vue';

export default {
  name: 'PageMain',
  components: {
    PageCard,
  },
  props: {
    arrFilms: Array,
    arrSeries: Array,
  },
  data() {
    return {
      baseImgUrl: 'https://image.tmdb.org/t/p/',
      imgSize: 'w342',
    };
  },
  methods: {
    generateUrl(path) {
      if (path) {
        return this.baseImgUrl + this.imgSize + path;
      }
      return null;
    },
    convertScore(score) {
      const maxScore = 5;
      const originalMaxScore = 10;
      return {
        score: Math.ceil((score * maxScore) / originalMaxScore),
        maxScore,
      };
    },
  },
};
</script>

<style lang="scss" scoped>
   div{
    min-height: 90vh;
    background-color: lightgray;
   }

</style>
