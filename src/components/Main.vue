<template>
  <div clas="container py-4">
    <div class="row row-cols-5 g-4 mx-5">
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
  },
  components: { MovieCard },
  data() {
    return {};
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";

ol {
  color: white;
}
</style>
