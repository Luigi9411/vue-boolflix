<template>
  <div>

  </div>
</template>

<script>

export default {
  name: 'PageMain',
  props: {
    arrFilms: Array,
    arrSeries: Array,
  },
};
</script>

<style lang="scss" scoped>
   div{
    min-height: 90vh;
    background-color: lightgray;
   }

</style>

https://api.themoviedb.org/3/search/movie?api_key=9776bd4da7d3b90c783bdbef13f8b137&query=ciao
