<template>
  <div id="app">
    <Header @search="updateSearch" />
    <Main
      :moviesList="moviesList"
      :popularList="popularList"
      :seriesList="seriesList"
      :moviesAndSeriesList="moviesAndSeriesList"
    />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  components: {
    Header,
    Main,
  },
  data() {
    return {
      apiKey: "?api_key=b2ef9be417192405baaaa7ce6bc2d036",
      popularList: [],
      moviesList: [],
      seriesList: [],
      moviesAndSeriesList: [],
      inputSearch: "",
    };
  },
  methods: {
    updateSearch(query) {
      if (query !== "") {
        this.popularList = [];
        this.inputSearch = query;
        this.getMoviesData();
        this.getSeriesData();
      } else {
        this.moviesList = [];
        this.seriesList = [];
        this.getPopularMoviesData();
      }
    },
    getMoviesData() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie${this.apiKey}&language=it-IT&query=${this.inputSearch}`
        )
        .then((response) => {
          console.log(response);
          this.moviesList = response.data.results;
          this.moviesAndSeriesList = [...this.moviesList, ...this.seriesList];
        })
        .catch((error) => {
          console.log(error.status_message);
        });
    },
    getSeriesData() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/tv${this.apiKey}&language=it-IT&query=${this.inputSearch}`
        )
        .then((response) => {
          console.log(response);
          this.seriesList = response.data.results;
          this.moviesAndSeriesList = [...this.moviesList, ...this.seriesList];
        })
        .catch((error) => {
          console.log(error.status_message);
        });
    },
    async getPopularMoviesData() {
      axios
        .get(
          `https://api.themoviedb.org/3/movie/popular${this.apiKey}&language=it-IT&page=1`
        )
        .then((response) => {
          console.log(response);
          this.popularList = response.data.results;
          console.log(this.popularList);
        })
        .catch((error) => {
          console.log(error.status_message);
        });
    },
  },
  created() {
    this.getPopularMoviesData();
  },
};
</script>

<style lang="scss">
@import "./assets/style/style.scss";

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #434343;
}
</style>
