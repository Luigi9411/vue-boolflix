<template>
  <div>
   <ul>
   <li>
    <img v-if="imgUrl" :src="imgUrl ? imgUrl : ''" :alt="title">
    <img v-else :src="imgUrl ? imgUrl : ''" :alt="title">
  </li>
   <li>{{ title }}</li>
   <li>{{ originalTitle }}</li>
   <li><lang-flag :iso="language" /></li>
   <li>{{ score }}</li>
  </ul>
  </div>
</template>

<script>
import LangFlag from 'flag-icons';

export default {
  nome: 'PageCard',
  components: {
    LangFlag,
  },
  props: {
    title: String,
    originalTitle: String,
    language: String,
    score: Object,
    imgUrl: String,
  },
};
</script>

<style lang="scss" scoped>
    ul{
      margin: 2em;
      padding: 1em;
      border: 1px solid green
    }
</style>
