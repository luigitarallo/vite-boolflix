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
      <h2>Movies</h2>
      <div
        v-if="this.store.movies.length > 0"
        class="row row-cols-1 row-cols-md-2 row-cols-lg-3 row-cols-xl-4 gy-3"
      >
        <!-- Add for cycle for print movie MediaCard -->
        <MediaCard
          v-for="movie in this.store.movies"
          :key="movie.id"
          :cardInfo="movie"
        />
      </div>
      <h4 v-else>No results found</h4>
    </section>
    <section>
      <h2>TV Series</h2>
      <div
        v-if="this.store.series.length > 0"
        class="row row-cols-2 row-cols-md-3 row-cols-lg-4 gy-3"
      >
        <!-- Add for cycle for print serie MediaCard -->
        <MediaCard
          v-for="serie in this.store.series"
          :key="serie.id"
          :cardInfo="serie"
        />
      </div>
      <h4 v-else>No results found</h4>
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

h4 {
  color: $brand-color;
  text-align: center;
}
</style>
