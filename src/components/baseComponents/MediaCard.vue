<script>
export default {
  props: { cardInfo: Object },
};
</script>

<template>
  <div class="col">
    <div class="media-card">
      <div class="media-card-content">
        <div class="media-card-img">
          <img
            v-if="cardInfo.cardImage != 'https://image.tmdb.org/t/p/w342null'"
            :src="cardInfo.cardImage"
            :alt="cardInfo.name"
          />
          <img
            v-else
            src="public\img\image-not-available.png"
            alt="generale image"
          />
        </div>

        <div class="media-card-info">
          <h2>Titolo: {{ cardInfo.name }}</h2>
          <h3>Titolo originale: {{ cardInfo.original_title }}</h3>
          <span
            >Lingua:<img
              :src="cardInfo.language"
              alt="language"
              class="flag-image"
            />
          </span>
          <p>{{ cardInfo.overview }}</p>

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
    </div>
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/scss/general.scss";

.media-card {
  background-color: transparent;
  perspective: 1000px;
  width: 100%;
  height: 460px;
}

.media-card-content {
  position: relative;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}
.media-card:hover .media-card-content {
  transform: rotateY(180deg);
}

.media-card-img,
.media-card-info {
  position: absolute;
  width: 100%;
  height: 460px;
  backface-visibility: hidden;
}

.media-card-img {
  object-fit: cover;

  img {
    max-width: 100%;
    height: 460px;
    object-fit: cover;
    border: 1px solid red;
    border-radius: 5px;
  }
}

.media-card-info {
  background-color: black;
  color: white;
  transform: rotateY(180deg);
  border-radius: 5px;
  border: 1px solid red;
  .flag-image {
    width: 30px;
  }
}

.media-card-info .star-full {
  color: yellow;
}
.star-empty {
  color: white;
}
</style>
