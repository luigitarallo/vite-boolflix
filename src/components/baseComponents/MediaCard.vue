<script>
export default {
  data() {
    return {
      text: "Example Card",
    };
  },
  props: { cardInfo: Object },
};
</script>

<template>
  <div class="card-body">
    {{ cardInfo.name }} - {{ cardInfo.original_title }} -
    {{ cardInfo.language }} - {{ cardInfo.vote }}
  </div>
</template>

<style lang="scss" scoped></style>
