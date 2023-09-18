<script>
import axios from "axios";
import { store } from "./data/store";
import {
  api,
  languageFlags,
  moviesUrl,
  seriesUrl,
  cardImgUrl,
} from "./data/staticData";

import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: { AppHeader, AppMain },

  methods: {
    fetchMedia(wordsToSearch) {
      axios
        .get(moviesUrl, {
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
              overview,
            } = movie;
            let flag = languageFlags[original_language];
            if (!flag) {
              flag = languageFlags.ud;
            }

            return {
              name: title,
              original_title,
              language: flag,
              vote: Math.ceil(vote_average / 2),
              id,
              cardImage: cardImgUrl + poster_path,
              overview,
            };
          });
        });
      axios
        .get(seriesUrl, {
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
              overview,
            } = serie;
            let flag = languageFlags[original_language];
            if (!flag) {
              flag = languageFlags.ud;
            }
            return {
              name,
              original_title: original_name,
              language: flag,
              vote: Math.ceil(vote_average / 2),
              id,
              cardImage: cardImgUrl + poster_path,
              overview,
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
