<template>
  <section>
    <button
      type="button"
      class="btn btn-primary watch_later"
      data-toggle="modal"
      data-target="#exampleModalLong"
    >
      Watch Later
    </button>
    <div
      class="modal fade"
      id="exampleModalLong"
      tabindex="-1"
      role="dialog"
      aria-labelledby="exampleModalLongTitle"
      aria-hidden="true"
    >
      <div class="modal-dialog" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <button
              type="button"
              class="close"
              data-dismiss="modal"
              aria-label="Close"
            >
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
            <div
              v-for="(watchLater, index) in watchLater"
              :key="index"
              class="col-md-12"
            >
              <div class="card" style="width: 18rem; margin: 1rem auto">
                <img
                  :src="
                    'https://image.tmdb.org/t/p/w1280' + watchLater.poster_path
                  "
                  class="card-img-top"
                  :alt="watchLater.title"
                />
                <div class="card-body">
                  <h5 class="card-title">{{ watchLater.title }}</h5>
                  <h4 class="card-text">
                    {{ watchLater.vote_average.toFixed(1) }}
                  </h4>
                  <h5 class="card-text">
                    {{ watchLater.release_date }}
                  </h5>
                  <button
                    v-on:click.prevent="removeMovie(index)"
                    class="btn btn-danger"
                  >
                    remove
                  </button>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  props: ["watchLater", "removeMovie"],
  mounted() {
    console.log(this.watchLater);
  },
};
</script>

<style>
.watch_later {
  margin: 0 0 0 auto;
  display: block;
}
</style>