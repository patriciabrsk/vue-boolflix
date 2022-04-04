<template>
  <div class="movie-card card">
    <img :alt="movieData.title" />
    <h1>{{ movieData.title }}</h1>
    <p>{{ movieData.original_title }}</p>
    <p></p>
    <p></p>
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
