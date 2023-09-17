<script>
import axios from "axios";
import { store } from "./data/store";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

const api = "8fa93795453909bcada8baee1989bfa4";

export default {
  data() {
    return {
      languageFlags: {
        it: "flags/italy.png",
        en: "flags/united-kingdom.png",
        fr: "flags/france.png",
        de: "flags/germany.png",
        pt: "flags/portugal.png",
        ja: "flags/japan.png",
        zh: "flags/china.png",
        ud: "flags/rainbow.png",
      },
    };
  },
  components: { AppHeader, AppMain },

  methods: {
    fetchMedia(wordsToSearch) {
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
              poster_path,
            } = movie;
            let flag = this.languageFlags[original_language];
            if (!flag) {
              flag = "flags/rainbow.png";
            }
            return {
              name: title,
              original_title,
              language: flag,
              vote: Math.ceil(vote_average / 2),
              id,
              cardImage: "https://image.tmdb.org/t/p/w342" + poster_path,
            };
          });
        });
      axios
        .get("https://api.themoviedb.org/3/search/tv", {
          params: {
            query: wordsToSearch,
            api_key: api,
          },
        })
        .then((response) => {
          store.series = response.data.results.map((serie) => {
            const {
              name,
              original_name,
              original_language,
              vote_average,
              id,
              poster_path,
            } = serie;
            let flag = this.languageFlags[original_language];
            if (!flag) {
              flag = "flags/rainbow.png";
            }
            return {
              name,
              original_title: original_name,
              language: flag,
              vote: Math.ceil(vote_average / 2),
              id,
              cardImage: "https://image.tmdb.org/t/p/w342" + poster_path,
            };
          });
        });
    },
  },
};
</script>

<template>
  <AppHeader @search-words="fetchMedia" />
  <AppMain />
</template>

<style lang="scss">
@use "./assets/scss/general.scss";
</style>
