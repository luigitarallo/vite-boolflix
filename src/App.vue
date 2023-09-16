<script>
import axios from "axios";
import { store } from "./data/store";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

const api = "8fa93795453909bcada8baee1989bfa4";

export default {
  components: { AppHeader, AppMain },

  methods: {
    fetchMovies(wordsToSearch) {
      axios
        .get("https://api.themoviedb.org/3/search/movie", {
          params: {
            query: wordsToSearch,
            api_key: api,
          },
        })
        .then((response) => {
          store.movies = response.data.results.map((movie) => {
            const {
              title,
              original_title,
              original_language,
              vote_average,
              id,
            } = movie;
            return {
              name: title,
              original_title,
              language: original_language,
              vote: Math.ceil(vote_average / 2),
              id,
            };
          });
        });
    },
  },
};
</script>

<template>
  <AppHeader @search-words="fetchMovies" />
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/general.scss";
</style>
