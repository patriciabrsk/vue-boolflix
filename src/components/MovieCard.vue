<template>
  <div class="justify-content-center d-flex">
    <div class="col">
      <div
        class="movie-card overflow-scroll bg-dark rounded-3 p-0"
        @click="isClicked = !isClicked"
      >
        <div class="front-image">
          <img
            v-show="!isClicked"
            class="rounded img-fluid"
            :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
            :alt="movieData.title"
          />
        </div>
        <div class="back-info p-3 text-white" v-show="isClicked">
          <h5 class="title text-uppercase fw-bold">
            {{ movieData.title || movieData.name }}
          </h5>
          <p class="original-title fst-italic fw-light">
            {{ movieData.original_title || movieData.original_name }}
          </p>
          <p class="overview">{{ movieData.overview }}</p>
          <p class="vote-average">
            {{ getRatingInteger(movieData.vote_average) }}
            <font-awesome-icon icon="fa-solid fa-star" />
          </p>
          <country-flag :country="movieData.original_language" size="small" />
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
  methods: {
    getRatingInteger(number) {
      return Math.ceil(number / 2);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/style.scss";

div.movie-card {
  width: 100%;
  // height: 500px;
  &:hover {
    transform: scale(1.01);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.6);
    cursor: pointer;
  }

  .front-image.clicked {
    display: none;
  }

  .movie-card .back-info {
  }

  div.front-image img {
    height: 100%;
    object-fit: cover;
  }
}
</style>
