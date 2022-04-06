<template>
  <div class="container-fluid p-4 mb-4">
    <div
      class="row row-cols-4 row-cols-md-5 row-cols-lg-6 g-4"
      v-if="moviesList.length > 0"
    >
      <MovieCard
        :movieData="movie"
        v-for="(movie, index) in moviesList"
        :key="index"
      />
    </div>
    <div
      class="row row-cols-4 row-cols-md-5 row-cols-lg-6 g-4"
      v-if="seriesList.length > 0"
    >
      <MovieCard
        :movieData="show"
        v-for="(show, index) in seriesList"
        :key="index"
      />
    </div>
    <div
      class="row row-cols-4 row-cols-md-5 row-cols-lg-6 g-4"
      v-if="popularList.length > 0"
    >
      <div class="col-12 col-12-lg text-white mb-0">
        <span class="badge text-uppercase fs-6 px-3 py-2 rounded-pill bg-dark">
          Most Popular
        </span>
      </div>
      <MovieCard
        :movieData="movie"
        v-for="(movie, index) in popularList"
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
    moviesAndSeriesList: Array,
    seriesList: Array,
    popularList: Array,
  },
  components: { MovieCard },
};
</script>

<style scoped lang="scss">
@import "../assets/style/style.scss";
</style>
