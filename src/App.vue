<template>
  <div id="app">
    <Header @search="search" />
    <Main />
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
      moviesList: [],
    };
  },
  methods: {
    search(query) {
      if (query != "") {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=b2ef9be417192405baaaa7ce6bc2d036&language=it-IT&query=${query}`
          )
          .then((response) => {
            this.movies = response.data.results;
            console.log(this.moviesList);
          })
          .catch((error) => {
            console.log(error.status_message);
          });
      }
    },
    // async getMovieData() {
    //   axios
    //     .get(
    //       `https://api.themoviedb.org/3/search/movie?api_key=b2ef9be417192405baaaa7ce6bc2d036&language=it-IT&`
    //     )
    //     .then((response) => {
    //       this.movies = response.data.results;
    //       console.log(this.moviesList);
    //     })
    //     .catch((error) => {
    //       console.log(error.status_message);
    //     });
    // },
  },
  // created() {
  //   this.getMovieData();
  // },
};
</script>

<style lang="scss">
body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  background-color: #434343;
}
</style>
