<template>
  <div>
    <div class="col">
      <div class="movie-card h-100">
        <!-- <div class="front"> -->
        <img
          class="img-fluid rounded-3"
          :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
          :alt="movieData.title"
        />
        <!-- <h1>{{ movieData.title }}</h1>
        <p>{{ movieData.original_title }}</p> -->
        <!-- </div> -->
      </div>
    </div>
    <!-- <div class="back"></div> -->
  </div>
  <!-- </div> -->
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    movieData: Object,
  },
  // props: {
  //   movieData: {
  //     type: String,
  //     required: true,
  //   },
  data() {
    return {};
  },
};
</script>

<style lang="scss" scoped></style>
