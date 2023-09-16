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
  <header class="container">
    <div class="input-group mb-3">
      <input
        v-model="searched"
        @keyup.enter="$emit('search-words', searched)"
        type="text"
        class="form-control"
        placeholder=""
        aria-describedby="button-addon2"
      />
      <button
        @click="$emit('search-words', searched)"
        class="btn btn-outline-secondary"
        type="button"
        id="button-addon2"
      >
        Search
      </button>
    </div>
  </header>
</template>

<style lang="scss"></style>
