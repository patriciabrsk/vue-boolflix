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
            v-if="movieData.poster_path"
            :src="`https://image.tmdb.org/t/p/w342${movieData.poster_path}`"
            :alt="movieData.title"
          />
          <img
            v-show="!isClicked"
            class="rounded img-fluid"
            v-else
            src="https://dummyimage.com/330x495/787878/fff.png&text=Poster+not+available"
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
          <country-flag :country="getLanguage()" size="small" />
          <p class="vote-average">
            <font-awesome-icon
              v-for="(star, int) in 5"
              :key="int"
              :icon="
                int < getRatingInteger(movieData.vote_average)
                  ? 'fa-solid fa-star'
                  : 'fa-regular fa-star'
              "
            />
          </p>
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
    getLanguage() {
      switch (this.movieData.original_language) {
        case "en":
          return "gb";
        case "ja":
          return "jp";
        case "zh":
          return "cn";
        default:
          return this.movieData.original_language;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/style.scss";

div.movie-card {
  &:hover {
    transform: scale(1.01);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.6);
    cursor: pointer;
  }

  .front-image.clicked {
    display: none;
  }

  div.front-image img {
    height: 100%;
    object-fit: cover;
  }
}
</style>
