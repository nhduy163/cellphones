<template>
  <div class="slide">
    <div v-if="isJpg === true" class="wrap__img--jpg">
      <nuxt-link to="/">
        <img class="img__jpg" :src="slides[handleCurrent].src" />
      </nuxt-link>
    </div>
    <div v-if="isJpg === false && singleWidth > 100" class="wrap__img--png">
      <nuxt-link to="/">
        <img class="img__png" :src="slides[handleCurrent].src" />
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    slides: { type: Array, default: () => [] },
    currentImg: { type: Number, default: 0 },
    isJpg: Boolean,
    singleWidth: { type: Number, default: 0 },
  },
  computed: {
    handleCurrent() {
      return Math.abs(this.currentImg) % this.slides.length
    },
  },
}
</script>

<style lang="scss">
.slide {
  position: relative;
  width: 100%;
  height: 100%;

  .wrap__img--jpg {
    position: relative;
    border-radius: 1rem;

    .img__jpg {
      display: block;
      width: 100%;
      height: auto;
      object-fit: cover;
      border-radius: 1rem;
      box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
        rgb(60 64 67 / 15%) 0px 2px 6px 2px;
    }
  }
  .wrap__img--png {
    height: 100%;
    object-fit: cover;
    .img__png {
      border-radius: 1rem;
      box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
        rgb(60 64 67 / 15%) 0px 2px 6px 2px;
      display: block;
      width: 100%;
      height: auto;
      object-fit: cover;
    }
  }
}
// @media only screen and (max-width: 1200px) {
//   .slide {
//     .wrap__img--png {
//       .img__png {
//         width: 100%;
//       }
//     }
//   }
// }
// @media only screen and (max-width: 600px) {
//   .slide {
//     .wrap__img--png {
//       .img__png {
//         width: 100%;
//       }
//     }
//   }
// }
//
</style>
