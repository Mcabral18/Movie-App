<template>
  <div class="container">
    <movies-list :movies="movies" />
  </div>
</template>

<script>
import MoviesList from "../components/MoviesList.vue";
export default {
  components: { MoviesList },
  data() {
    return {
      movies: [],
    };
  },
  async mounted() {
    const API_URL =
      "https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=04c35731a5ee918f014970082a0088b1&page=1";

    const response = await fetch(`${API_URL}`);
    const data = await response.json();
    this.movies = data.results;
    console.log(this.movies);
  },
};
</script>

<style>
</style>