<script>
export default {
  props: { cardInfo: Object },
};
</script>

<template>
  <div class="col">
    <div class="media-image">
      <img
        v-if="cardInfo.cardImage != 'https://image.tmdb.org/t/p/w342null'"
        :src="cardInfo.cardImage"
        alt=""
      />
      <img v-else src="img/not-found-icon.jpg" alt="" />
    </div>
    <div class="d-none">
      {{ cardInfo.name }}
      <div class="flag-image">
        <img :src="cardInfo.language" alt="" />
      </div>
      {{ cardInfo.original_title }} -
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
  </div>
</template>

<style lang="scss" scoped>
col {
  width: 100%;
  height: 100%;
}
.media-image {
  display: flex;
  align-items: center;
  width: 100%;
  height: 100%;
  img {
    border: 1px solid red;
    border-radius: 5px;
    object-fit: cover;
  }
  .media-not-found {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
  }
}
.flag-image {
  height: 30px;
  width: 30px;
}
.star-full {
  color: yellow;
}
.star-empty {
  color: black;
}
</style>
