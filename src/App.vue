<script>
import { store } from "./data/store";
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  data() {
    return {
      store: store,
    };
  },
  components: { AppHeader, AppMain },
};
</script>

<template>
  <AppHeader />
</template>

<style lang="scss">
@use "./assets/scss/general.scss";
</style>
