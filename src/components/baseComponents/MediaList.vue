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
  <MediaCard :store="store" />
</template>

<style lang="scss" scoped></style>
