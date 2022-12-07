<template>
  <div class="flip-card">
    <div class="flip-card-inner">
      <div class="flip-card-front">
        <img
          v-if="imgUrl"
          :src="imgUrl"
          :alt="title"
        >
        <img
          v-else
          src="@/assets/img/default.jpg"
          :alt="title"
        >
      </div>

      <div class="flip-card-back">
        <div>
          Titolo: {{ title }}
        </div>
        <div>
          Titolo originale: {{ originalTitle }}
        </div>

        <lang-flag :iso="language" />
        <div class="language-textual">
          {{ language }}
        </div>

        <div class="score">
          <font-awesome-icon
            v-for="i in score.score"
            :key="i"
            icon="fa-solid fa-star"
            :style="{ color: 'yellow' }"
          />
          <font-awesome-icon
            v-for="i in (score.maxScore - score.score)"
            :key="(i + score.maxScore)"
            icon="fa-regular fa-star"
            :style="{ color: 'yellow' }"
          />
        </div>

        <div class="cast">
          Cast: {{ cast.join(', ') }}
        </div>

        <p>
          <!-- eslint-disable-next-line -->
          Lorem ipsum dolor ssectetur adiplitia ipsum,. Lorem ipsum dolor sit amet consectetur adipisicing elit. Ipsum modi beatae ea et cum quae nemo, sunt odio vitae enim itaque voluptatibus unde explicabo quia praesentium ut facere a natus.
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from 'vue-lang-code-flags';

export default {
  name: 'PageCard',
  components: {
    LangFlag,
  },
  props: {
    title: String,
    originalTitle: String,
    language: String,
    score: Object,
    imgUrl: String,
    cast: {
      type: Array,
      default() {
        return [];
      },
    },
  },
};
</script>

<style lang="scss" scoped>
  .flip-card {
    padding: 1rem;
  }
  img {
    width: 100%;
    height: 100%;
    object-fit: cover;
    object-position: center;
  }
  .flag-icon-undefined,
  .language-textual {
    display: none;
  }
  .flag-icon-undefined ~ .language-textual {
    display: block;
  }
.flip-card {
  height: 700px;
  perspective: 1000px;
}

.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
.flip-card-back {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
  overflow-y: auto;
  padding: 4em 1em;
  border: 2px solid white;
}
</style>
