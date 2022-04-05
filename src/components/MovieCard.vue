<template>
  <div>
    <div class="col">
      <div class="movie-card h-100 card rounded-3">
        <!-- <div class="front"> -->
        <img
          class="img-fluid"
          :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
          :alt="movieData.title"
        />
        <h1 class="text-white">{{ movieData.title || movieData.name }}</h1>
        <country-flag country="it" size="big" />
        <p class="text-white">
          {{ movieData.original_title || movieData.original_name }}
        </p>
        <p class="text-white">{{ movieData.original_language }}</p>
        <!-- </div> -->
        <!-- <div class="back"></div> -->
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
};
</script>

<style lang="scss" scoped>
div.movie-card:hover {
  transform: scale(1.01);
  cursor: pointer;
}
</style>
