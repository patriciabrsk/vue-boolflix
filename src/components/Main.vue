<template>
  <div>
    <!-- <MovieCard
        :movieData="movie"
        v-for="(movie, index) in moviesList"
        :key="index"
      />
    </div> -->
    <ol
      v-for="(movie, index) in moviesList"
      :key="index"
      class="text-uppercase p-3"
    >
      <li>
        {{ movie.title }}
      </li>
      <li>
        {{ movie.original_title }}
      </li>
      <li>
        {{ movie.original_language }}
      </li>
      <li>
        {{ movie.vote_average }}
      </li>
    </ol>
  </div>
</template>

<script>
// import MovieCard from "./MovieCard.vue";

export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: "Main",
  props: {
    moviesList: Array,
  },
  //   components: { MovieCard },
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
