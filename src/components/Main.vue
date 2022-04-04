<template>
  <div>
    <div>
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
  props: {},
  components: { MovieCard },
  data() {
    return {};
  },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";
</style>
