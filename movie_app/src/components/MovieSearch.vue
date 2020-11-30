<template>
  <div class="col-md-4">
    <div class="card" style="width: 18rem">
      <img
        :src="'https://image.tmdb.org/t/p/w1280' + movieSearch.poster_path"
        class="card-img-top"
        :alt="movieSearch.title"
      />
      <div class="card-body">
        <h5 class="card-title">{{ movieSearch.title }}</h5>
        <h4 class="card-text">
          {{ movieSearch.vote_average.toFixed(1) }}
        </h4>
        <h5 class="card-text">
          {{ movieSearch.release_date }}
        </h5>
        <button class="btn btn-primary">Watch Latter</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: ["movieSearch"],
};
</script>

<style>
</style>