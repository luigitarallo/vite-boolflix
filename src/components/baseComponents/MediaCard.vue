<script>
export default {
  data() {
    return {
      text: "Example Card",
    };
  },
  props: { store: Object },
};
</script>

<template>
  <div v-for="movie in store.movies" :key="movie.id" class="card">
    <div class="card-body">
      {{ movie.name }} - {{ movie.original_title }} - {{ movie.language }} -
      {{ movie.vote }} -
      {{ movie.id }}
    </div>
  </div>
</template>

<style lang="scss" scoped></style>
