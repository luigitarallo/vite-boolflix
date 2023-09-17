<script>
export default {
  data() {
    return {
      searched: "",
    };
  },
  emits: ["search-words"],
};
</script>

<template>
  <header>
    <div class="container d-flex justify-content-between align-items-center">
      <img src="img/netflix-logo.png" alt="" class="logo" />
      <div class="input-group">
        <input
          v-model="searched"
          @keyup.enter="$emit('search-words', searched)"
          type="text"
          class="form-control"
          placeholder="Scrivi qui"
          aria-describedby="button-addon2"
        />
        <button
          @click="$emit('search-words', searched)"
          class="btn btn-outline-secondary"
          type="button"
          id="button-addon2"
        >
          Cerca qualcosa
        </button>
      </div>
    </div>
  </header>
</template>

<style lang="scss">
header {
  background-color: black;
  padding: 1rem 1rem;
  .logo {
    width: 15%;
    display: block;
  }
  .input-group {
    width: 30%;
  }
}
</style>
