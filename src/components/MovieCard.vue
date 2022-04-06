<template>
  <div class="justify-content-center d-flex">
    <div class="col">
      <div class="movie-card rounded-3 p-0" @click="isClicked = !isClicked">
        <div class="front-image">
          <img
            v-show="!isClicked"
            class="rounded"
            :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
            :alt="movieData.title"
          />
        </div>
        <div class="back-info overflow-auto p-3" v-show="isClicked">
          <h5 class="title text-white text-uppercase">
            Titolo: {{ movieData.title || movieData.name }}
          </h5>
          <p class="original-title text-white">
            Titolo originale:
            {{ movieData.original_title || movieData.original_name }}
          </p>
          <p class="overview">{{ movieData.overview }}</p>
          <country-flag :country="movieData.original_language" size="small" />
          <p>{{ movieData.vote_average }}</p>
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
      isClicked: false,
    };
  },
  // methods: {
  //   showBack() {
  //     this.isClicked = !this.isClicked;
  //   },
  // },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/style.scss";

div.movie-card {
  position: relative;

  &:hover {
    transform: scale(1.01);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.6);
    cursor: pointer;
  }

  .front-image.clicked {
    display: none;
  }

  .movie-card .back-info {
    color: white;
    position: absolute;
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.16), 0 2px 5px rgba(0, 0, 0, 0.26);
  }

  div.front-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
