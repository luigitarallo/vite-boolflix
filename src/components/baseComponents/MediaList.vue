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
  <MediaCard
    v-for="movie in store.movies"
    :key="movie.id"
    class="card"
    :cardInfo="movie"
  />
</template>

<style lang="scss" scoped></style>
