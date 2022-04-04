<template>
  <div class="movie-card rounded-3">
    <div class="front">
      <img
        :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
        :alt="movieData.title"
      />
      <h1>{{ movieData.title }}</h1>
      <p>{{ movieData.original_title }}</p>
      <p></p>
      <p></p>
    </div>

    <!-- <div class="back"></div> -->
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    movieData: {
      type: String,
      required: true,
    },
    data() {
      return {};
    },
  },
};
</script>

<style lang="scss" scoped></style>
