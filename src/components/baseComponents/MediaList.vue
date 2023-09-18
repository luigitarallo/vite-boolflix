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
    <section>
      <h2>Film</h2>
      <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3">
        <MediaCard
          v-for="movie in store.movies"
          :key="movie.id"
          :cardInfo="movie"
        />
      </div>
    </section>
    <section>
      <h2>Serie TV</h2>
      <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3">
        <MediaCard
          v-for="serie in store.series"
          :key="serie.id"
          :cardInfo="serie"
        />
      </div>
    </section>
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/scss/general.scss";
h2 {
  color: white;
  padding: 1rem 0;
}
</style>
