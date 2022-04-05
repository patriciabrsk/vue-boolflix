<template>
  <div clas="container p">
    <div class="row row-cols-4 g-4">
      <MovieCard
        :movieData="movie"
        v-for="(movie, index) in moviesList"
        :key="index"
      />
    </div>
  </div>
</template>

<script>
import MovieCard from "./MovieCard.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Main",
  props: {
    moviesList: Array,
    popularList: Array,
  },
  components: { MovieCard },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";
</style>
