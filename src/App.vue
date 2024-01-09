<script>
// Import axios
import axios from "axios";

// Import reactive data
import { store } from "./data/store";
// Import static data
import {
  api,
  languageFlags,
  moviesUrl,
  seriesUrl,
  cardImgUrl,
} from "./data/staticData";

// Import components
import AppHeader from "./components/AppHeader.vue";
import AppMain from "./components/AppMain.vue";

export default {
  components: { AppHeader, AppMain },

  methods: {
    // Method for search therms with api
    fetchMedia(wordsToSearch) {
      // Call for Movies
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
            // Return Mapped object with custom key and value
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
      // Call for Series
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
            // Return Mapped object with custom key and value

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
@use "./assets/scss/general.scss" as *;
@use "./assets/scss/partials/variables" as *;

// Custom Scrollbar

::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: $brand-color;
  border-radius: 10px;
  width: 1px;
}

::-webkit-scrollbar-thumb:hover {
  background: #555;
  border-radius: 10px;
}
</style>
