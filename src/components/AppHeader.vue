<script>
export default {
  data() {
    return {
      searched: "",
    };
  },
  // Regitered emits
  emits: ["search-words"],
};
</script>

<template>
  <header>
    <div class="container d-flex justify-content-between align-items-center">
      <img src="img/netflix-logo.png" alt="" class="logo" />
      <div class="input-group">
        <!-- Add v-model on input to get the input text -->
        <!-- Add v-on keyup.enter to send the input text on button press -->
        <input
          v-model="searched"
          @keyup.enter="$emit('search-words', searched)"
          type="text"
          class="form-control"
          placeholder="Search something"
          aria-describedby="button-addon2"
        />
        <!-- Add v-on click to send the input text on button press -->
        <button
          @click="$emit('search-words', searched)"
          class="btn btn-outline-danger"
          type="button"
          id="button-addon2"
        >
          Search
        </button>
      </div>
    </div>
  </header>
</template>

<style lang="scss">
@use "../assets/scss/general.scss" as *;
@use "../assets/scss/partials/variables" as *;

header {
  background-color: $header-bg;
  padding: 1rem 1rem;
  .logo {
    width: 15%;
    display: block;
  }
  .input-group {
    width: 30%;
  }
  @media screen and (max-width: 992px) {
    .input-group {
      width: 50%;
    }
  }

  @media screen and (max-width: 600px) {
    .input-group {
      width: 80%;
    }
  }
}
</style>
