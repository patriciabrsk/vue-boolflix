<template>
  <div class="justify-content-center d-flex">
    <div class="col">
      <div
        class="movie-card rounded-3 p-0"
        @click="flipCard()"
        :class="{ flipped: isClicked }"
      >
        <div class="flip-card-wrapper">
          <div class="front-image">
            <img
              class="rounded"
              :src="`https://image.tmdb.org/t/p/w342/${movieData.poster_path}`"
              :alt="movieData.title"
            />
          </div>
          <div class="back-info d-none overflow-auto">
            <h2 class="title text-white">
              Titolo: {{ movieData.title || movieData.name }}
            </h2>
            <p class="original-title text-white">
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
    flipCard() {
      this.isClicked = !this.isClicked;
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/style/style.scss";

div.movie-card {
  -webkit-transition: -webkit-transform 0.6s;
  -moz-transition: -moz-transform 0.6s;
  -o-transition: -o-transform 0.6s;
  transition: transform 0.6s;
  -webkit-transform-style: preserve-3d;
  -moz-transform-style: preserve-3d;
  -o-transform-style: preserve-3d;
  transform-style: preserve-3d;
  position: relative;

  &:hover {
    transform: scale(1.01);
    box-shadow: 0 5px 15px rgba(0, 0, 0, 0.6);
    cursor: pointer;
  }

  .movie-card.flipped {
    -webkit-transform: rotateY(180deg);
    transform: rotateY(180deg);
  }

  .movie-card .front-image,
  .movie-card .back-info {
    color: white;
    position: absolute;
    -webkit-backface-visibility: hidden;
    backface-visibility: hidden;
    box-shadow: 3px 5px 20px 2px rgba(0, 0, 0, 0.25);
    -webkit-box-shadow: 0 2px 10px rgba(0, 0, 0, 0.16),
      0 2px 5px rgba(0, 0, 0, 0.26);
    box-shadow: 0 2px 10px rgba(0, 0, 0, 0.16), 0 2px 5px rgba(0, 0, 0, 0.26);
  }

  div.front-image img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
}
</style>
