<template>
  <div id="app">
    <nav-bar />
    <movies />
  </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import Movies from "./views/Movies.vue";
export default {
  name: "App",
  components: { NavBar, Movies },
};
</script>

<style>
</style>
