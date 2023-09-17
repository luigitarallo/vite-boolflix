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

    <div class="media-image">
      <img :src="cardInfo.cardImage" alt="" />
    </div>

    {{ cardInfo.name }} {{ cardInfo.original_title }} -
    <div class="stars">
      <font-awesome-icon
        icon="fa-solid fa-star"
        v-for="n in cardInfo.vote"
        :key="cardInfo.id"
        class="star-full"
      />

      <font-awesome-icon
        icon="fa-solid fa-star"
        v-for="n in 5 - cardInfo.vote"
        :key="cardInfo.id"
        class="star-empty"
      />
    </div>
  </div>
</template>

<style lang="scss" scoped>
.flag-image {
  height: 30px;
  width: 30px;
  img {
    max-width: 100%;
  }
}
.star-full {
  color: yellow;
}
.star-empty {
  color: black;
}
</style>
