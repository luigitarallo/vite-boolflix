<script>
export default {
  data() {
    return {
      searchedTerm: "",
    };
  },
  emits: ["searchWords"],
};
</script>

<template>
  <header class="container">
    <div class="input-group mb-3">
      <input
        v-model="searchedTerm"
        @keyup.enter="$emit('searchWords', searchedTerm)"
        type="text"
        class="form-control"
        placeholder=""
        aria-describedby="button-addon2"
      />
      <button
        @click="$emit('searchWords', searchedTerm)"
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
