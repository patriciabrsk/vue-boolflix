<template>
  <div class="justify-content-center d-flex">
    <div class="col">
      <div class="movie-card h-100 rounded-3">
        <div class="front-image">
          <img
            class="img-fluid rounded-3"
            :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
            :alt="movieData.title"
          />
        </div>
        <div class="back-info d-none">
          <h2 class="text-white title">
            Titolo: {{ movieData.title || movieData.name }}
          </h2>
          <p class="text-white original-title">
            Titolo originale:
            {{ movieData.original_title || movieData.original_name }}
          </p>
          <p class="overview">{{ movieData.overview }}</p>
          <country-flag :country="movieData.original_language" size="small" />
          <p></p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "MovieCard",
  props: {
    movieData: Object,
  },
  data() {
    return {
      hover: false,
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/style.scss";
.active {
}
div.movie-card {
  border: 2px solid transparent;
  &:hover {
    border: 2px solid red;
    transform: scale(1.01);
    cursor: pointer;
  }
}
</style>
