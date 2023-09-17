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
  <div>
    <h2>Film</h2>
    <MediaCard
      v-for="movie in store.movies"
      :key="movie.id"
      class="card"
      :cardInfo="movie"
    />
  </div>
  <div>
    <h2>Serie TV</h2>
    <MediaCard
      v-for="serie in store.series"
      :key="serie.id"
      class="card"
      :cardInfo="serie"
    />
  </div>
</template>

<style lang="scss" scoped></style>
