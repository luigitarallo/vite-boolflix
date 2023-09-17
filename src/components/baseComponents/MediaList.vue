<script>
import { store } from "../../data/store";
import MediaCard from "./MediaCard.vue";

export default {
  data() {
    return {
      store,
    };
  },
  components: { MediaCard },
};
</script>

<template>
  <div class="container">
    <h2>Film</h2>
    <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3">
      <MediaCard
        v-for="movie in store.movies"
        :key="movie.id"
        class="card"
        :cardInfo="movie"
      />
    </div>
  </div>
  <div class="container">
    <h2>Serie TV</h2>
    <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3">
      <MediaCard
        v-for="serie in store.series"
        :key="serie.id"
        class="card"
        :cardInfo="serie"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
