<template>
  <div>
    <div v-for="(movie, index) in moviesList" :key="index">
      <MovieCard :movieData="movie" />
    </div>
  </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Main",
  props: {
    movies: [],
  },
  components: { MovieCard },
  data() {
    return {
      moviesList: [],
    };
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";
</style>
