<template>
  <section>
    <watch-later
      :watchLater="watchLater"
      :removeMovie="removeMovie"
      class="mt-3"
    />
    <div class="mt-3">
      <form @submit.prevent="getMovie">
        <fieldset class="form-group">
          <input
            v-model="searchMovie"
            type="text"
            class="form-control"
            id="searchTerm"
            placeholder="Search a Movie Title"
          />
        </fieldset>
      </form>
    </div>
    <div class="container">
      <div class="row">
        <movie-search
          class="mt-5"
          v-for="(movieSearch, index) in movieSearch"
          :key="index"
          :movieSearch="movieSearch"
          :addMovieSearch="addMovieSearch"
        />
      </div>
    </div>
    <div class="row" v-if="show">
      <movie
        v-for="(movie, index) in movies"
        :key="index"
        :movie="movie"
        :addMovie="addMovie"
      />
    </div>
  </section>
</template>

<script>
import Movie from "./Movie";
import MovieSearch from "./MovieSearch.vue";
import WatchLater from "./WatchLater.vue";
export default {
  props: ["movies"],
  data() {
    return {
      searchMovie: "",
      movieSearch: [],
      show: true,
      watchLater: [],
    };
  },
  components: {
    Movie,
    MovieSearch,
    WatchLater,
  },
  methods: {
    async getMovie() {
      const response = await fetch(
        `https://api.themoviedb.org/3/search/movie?&api_key=04c35731a5ee918f014970082a0088b1&query=${this.searchMovie}`
      );
      const data = await response.json();
      this.movieSearch = data.results;
      this.show = false;
      console.log(this.movieSearch);
    },
    addMovie(movie) {
      this.watchLater.push(movie);
      console.log(this.watchLater);
    },
    addMovieSearch(movieSearch) {
      this.watchLater.push(movieSearch);
      console.log(this.watchLater);
    },
    removeMovie(index) {
      this.watchLater.splice(this.watchLater.indexOf(index), 1);
    },
  },
};
</script>

<style>
</style>