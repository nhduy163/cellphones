<template>
  <div class="container">
    <main-header />
    <div class="slider-container">
      <div class="background-sm"></div>
      <sidebar-menu class="sidebar-menu" />
      <slider-ads :photo="photo" />
      <div class="banner-container">
        <NuxtLink to="/" class="banner">
          <img
            src="@/assets/images/banner.png"
            alt="banner"
            class="banner-content" />
          <img
            id="center"
            src="@/assets/images/banner2.png"
            alt="banner 2"
            class="banner-content" />
          <img
            src="@/assets/images/banner3.png"
            alt="banner 3"
            class="banner-content"
        /></NuxtLink>
      </div>
    </div>
    <div class="ads-container">
      <nuxt-link to="/">
        <img
          src="@/assets/images/banner-lg.png"
          alt="banner 4"
          class="ads-lg"
        />
        <img
          src="@/assets/images/banner-sm.png"
          alt="banner 4"
          class="ads-sm"
        />
      </nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  async asyncData({ $content, params }) {
    const photo = await $content('photo', params.slug).fetch()
    return { photo }
  },
}
</script>
<style lang="scss" scoped>
.container {
  .slider-container {
    position: relative;
    display: grid;
    grid-template-columns: 19% 56% 25%;
    height: 100%;
    width: 65%;
    margin: 5em auto 0;
    .background-sm {
      display: none;
    }
  }
  .banner-container {
    max-height: 10em;
    margin-left: 1em;
    .banner-content {
      height: 74%;
      min-width: 100%;
      border-radius: 8px;
      box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
        rgb(60 64 67 / 15%) 0px 2px 6px 2px;
    }
    #center {
      margin: 1em 0 1em;
    }
  }
  .ads-container {
    width: 65%;
    margin: 1em auto 0;
    .ads-sm {
      display: none;
    }
    img {
      border-radius: 12px;
      min-width: 100%;
      border-radius: 12px;
      box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
        rgb(60 64 67 / 15%) 0px 2px 6px 2px;
    }
  }
}
@media only screen and (max-width: 560px) {
  .container {
    .slider-container {
      position: relative;
      display: block;
      height: 100%;
      width: 100%;
      margin: 6.5em auto 0;
      .background-sm {
        width: 100%;
        height: 3.2em;
        display: block;
        position: absolute;
        border-radius: 0 0 15px 15px;
        background: linear-gradient(
          0deg,
          rgba(238, 147, 149, 1) 0%,
          rgba(236, 147, 148, 1) 100%
        );
      }
    }
    .banner-container {
      display: none;
    }
    .sidebar-menu {
      display: none;
    }
  }
  .ads-container {
    width: 93% !important;
    margin: 5em auto 0;
    border-radius: 12px;
    box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
      rgb(60 64 67 / 15%) 0px 2px 6px 2px;
    img {
      width: 10vw;
    }
    .ads-lg {
      display: none;
    }
    .ads-sm {
      display: block !important;
    }
  }
}
</style>