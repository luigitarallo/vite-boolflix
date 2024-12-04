<script>
export default {
  // Registered props
  props: { cardInfo: Object },
};
</script>

<template>
  <div class="col">
    <div class="media-card">
      <div class="media-card-content">
        <div class="media-card-img">
          <!-- Add v-if to show img if exists -->
          <img
            v-if="cardInfo.cardImage != 'https://image.tmdb.org/t/p/w342null'"
            :src="cardInfo.cardImage"
            :alt="cardInfo.name"
          />
          <!-- Add v-els to show default img if gotten cardImage is null -->

          <img v-else src="/img/image-not-available.png" alt="general image" />
        </div>

        <div class="media-card-info">
          <div class="container-info">
            <h2><span class="title">Title:</span> {{ cardInfo.name }}</h2>
            <h3>
              <span class="original-title">Original Title:</span>
              {{ cardInfo.original_title }}
            </h3>
            <span
              >Language:<img
                :src="cardInfo.language"
                alt="language"
                class="flag-image"
              />
            </span>
            <!-- Add v-if to show overview if exists -->
            <p v-if="cardInfo.overview != ''">
              <span class="plot">Plot:</span> {{ cardInfo.overview }}
            </p>
            <!-- Add v-else to show default plot if gotten overview is empty -->
            <p v-else><span class="plot">Plot:</span> Plot not available</p>

            <div class="vote">
              <span>Vote Average:</span>
              <!-- Add v-for to print filled star -->

              <font-awesome-icon
                icon="fa-solid fa-star"
                v-for="n in cardInfo.vote"
                :key="cardInfo.id"
                class="star-full"
              />
              <!-- Add v-for to print remaining empty stars -->
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
  </div>
</template>

<style lang="scss" scoped>
@use "../../assets/scss/general.scss" as *;
@use "../../assets/scss/partials/variables" as *;
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
    width: 100%;
    height: 460px;
    object-fit: cover;
    border: $brand-color;
    border-radius: 5px;
    border: 1px solid $brand-color;
  }
}

.media-card-info {
  background-color: $header-bg;
  color: $text-color;
  transform: rotateY(180deg);
  border-radius: 5px;
  border: 1px solid $brand-color;
  overflow-y: auto;
  .container-info {
    padding: 1rem;
    h2 {
      font-size: 1.6rem;
      .title {
        color: $brand-color;
      }
    }
    h3 {
      font-size: 1rem;
      .original-title {
        color: $brand-color;
      }
    }
  }
  .plot {
    color: $brand-color;
    font-weight: 900;
  }
  .flag-image {
    width: 30px;
    margin-left: 1rem;
  }
}

.vote {
  span {
    margin-right: 0.5rem;
  }
  .star-full {
    color: $star-full-color;
  }
  .star-empty {
    color: $star-empty-color;
  }
}
</style>
