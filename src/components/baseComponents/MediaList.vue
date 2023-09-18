<script>
// Import reactive data
import { store } from "../../data/store";

// Import component
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
  <div class="container my-3">
    <section>
      <h2>Film</h2>
      <div class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3">
        <!-- Add for cycle for print movie MediaCard -->
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
        <!-- Add for cycle for print serie MediaCard -->
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
// Import scss style
@use "../../assets/scss/general.scss" as *;
@use "../../assets/scss/partials/variables" as *;
h2 {
  color: $text-color;
  padding: 1rem 0;
}
</style>
