<template>
  <div class="col-md-4">
    <div class="card" style="width: 18rem">
      <img
        :src="'https://image.tmdb.org/t/p/w1280' + movie.poster_path"
        class="card-img-top"
        :alt="movie.title"
      />
      <div class="card-body">
        <h5 class="card-title">{{ movie.title }}</h5>
        <h4 class="card-text">
          {{ movie.vote_average.toFixed(1) }}
        </h4>
        <h5 class="card-text">
          {{ movie.release_date }}
        </h5>
        <button v-on:click="addMovie(movie)" class="btn btn-primary">
          Watch Latter
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["movie", "addMovie"],
};
</script>

<style >
.card {
  margin: 2rem 0;
  text-align: center;
}
</style>