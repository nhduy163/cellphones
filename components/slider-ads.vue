<template>
  <section class="slider">
    <transition tag="div" class="slider__image" name="slide">
      <div v-for="number in [currentImg]" :key="number">
        <SlideImage
          :slides="slides"
          :is-jpg="checkJpg"
          :current-img="currentImg"
          :single-width="singleWidth"
        />
      </div>
    </transition>
    <div v-if="singleWidth > 760" class="slider__nav">
      <div
        v-for="(slide, index) in slides"
        :key="index"
        class="nav__number"
        :class="checkIfClassActive(index)"
        @click="goToSlide(index)"
      >
        <div class="slideContent__text">
          <p class="slideContent__item">{{ slides[index].item }}</p>
          <p class="slideContent__slogan">{{ slides[index].slogan }}</p>
        </div>
      </div>
    </div>
    <div v-if="singleWidth < 760" class="slider__dot">
      <span
        v-for="(slide, index) in slides"
        :key="index"
        class="nav__dot"
        :class="checkIfClassActive(index)"
        @click="goToSlide(index)"
      >
      </span>
    </div>
  </section>
</template>

<script>
import SlideImage from './partials/slideImage'

export default {
  components: {
    SlideImage,
  },
  props: {
    photo: { type: Array, default: () => [] },
  },
  data() {
    return {
      isActive: 0,
      currentImg: 1,
      singleWidth: 0,
      timer: null,
      isJpg: true,
      slides: this.photo,
    }
  },
  computed: {
    checkJpg() {
      if (
        !this.slides[
          Math.abs(this.currentImg) % this.slides.length
        ].src.includes('jpg')
      ) {
        return false
      } else {
        return true
      }
    },
  },
  beforeMount() {
    window.addEventListener('resize', this.handleResize)
    this.handleResize()
  },
  mounted() {
    this.timer = setInterval(() => {
      this.currentImg = this.currentImg + 1
    }, 60000)
  },
  beforeDestroy() {
    window.removeEventListener('resize', this.handleResize)
  },
  methods: {
    checkIfClassActive(index) {
      if (index === Math.abs(this.currentImg) % this.slides.length) {
        return 'active'
      } else return ''
    },
    goToSlide(index) {
      clearInterval(this.timer)
      this.currentImg = index
      this.timer = setInterval(() => {
        this.currentImg = this.currentImg + 1
      }, 60000)
    },

    handleResize() {
      this.singleWidth = window.innerWidth
    },
  },
}
</script>

<style lang="scss" scoped>
.slide-enter-active {
  transition: 0.5s;
}
.slide-leave-active {
  position: absolute;
  transition: 0.5s;
}
.slide-enter {
  transform: translate(100%, 0);
}
.slide-leave-to {
  transform: translate(-100%, 0);
}
.slider {
  height: auto;
  width: 100%;
  overflow: hidden;
  position: relative;
  margin: 0 auto 0;
  border-radius: 1rem;
  box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
    rgb(60 64 67 / 15%) 0px 2px 6px 2px;
  .slider__image {
    position: relative;
  }
  .slider__nav {
    position: relative;
    display: flex;
    height: 7.4em;
    font-size: 12px;
    .nav__number {
      border-color: red;
      cursor: pointer;
      flex-basis: 20%;

      &:hover {
        background-color: #f3f4f6;
      }
      .slideContent__text {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        text-align: center;
        height: 100%;
        font-weight: 400;
        font-size: 12px;
        line-height: 20px;
        height: 100%;
        padding: 2px;
      }
    }
    .nav__number.active {
      background-color: #f3f4f6;

      .slideContent__text {
        font-weight: 700;
      }
    }
  }
  .slider__dot {
    display: flex;
    justify-content: center;
    margin-top: 1em;
    .nav__dot {
      height: 8px;
      width: 8px;
      background-color: #707070;
      border-radius: 50%;
      display: inline-block;
      margin: 0 0.3em 0;
    }
    .nav__dot.active {
      background-color: #d70018;
      width: 18px;
      height: 8px;
      border-radius: 10px;
      transition: 0.3s;
    }
  }
}
@media only screen and (max-width: 1600px) {
  .slider {
    width: 50%;
    z-index: 2;
    border-radius: 0;
    box-shadow: none;
    .slider__image {
      position: relative;
    }
    .slider__nav {
      .nav__number {
        font-size: 10;
      }
    }
  }
}

@media only screen and (max-width: 560px) {
  .slider {
    width: 93%;
    z-index: 2;
  }
}
</style>
