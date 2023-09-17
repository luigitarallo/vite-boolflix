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
    <div class="flag-image"><img :src="cardInfo.language" alt="" /></div>

    {{ cardInfo.name }} {{ cardInfo.original_title }} -
    {{ cardInfo.vote }}
  </div>
</template>

<style lang="scss" scoped>
.flag-image {
  height: 30px;
  width: 30px;
}
img {
  max-width: 100%;
}
</style>
