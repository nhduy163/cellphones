<template>
  <div class="background" :class="{ active: isInput }">
    <div class="header">
      <div class="header-container">
        <img
          src="@/assets/images/menu.svg"
          alt="menu icon"
          class="header-icon"
        />
        <NuxtLink to="/" class="header-logo"
          ><img src="@/assets/images/logo.svg" alt="logo cellphones"
        /></NuxtLink>
        <location-select />
        <div class="header-input">
          <span class="fa fa-search"></span>
          <input
            v-click-outside="hide"
            placeholder="Bạn cần tìm gì?"
            @click="toggleShow"
          />
        </div>
        <ul class="services">
          <li class="services-phone">
            <img src="@/assets/images/phone.svg" class="services-icon" />
            <div class="services-text">
              <p>Gọi mua hàng <b>1800.2044</b></p>
            </div>
          </li>
          <li class="services-close">
            <img src="@/assets/images/loca.svg" class="services-icon" />
            <div class="services-text">
              <p>
                Cửa hàng <br />
                Gần bạn
              </p>
            </div>
          </li>
          <li class="services-delivery">
            <img src="@/assets/images/car.svg" class="services-icon" />
            <div class="services-text">
              <p>
                Tra cứu <br />
                đơn hàng
              </p>
            </div>
          </li>
          <li class="services-cart">
            <img src="@/assets/images/cart.svg" class="services-icon" />
            <div class="services-text">
              <p>Giỏ hàng</p>
            </div>
          </li>
          <li class="services-login">
            <img src="@/assets/images/login.svg" class="services-icon" />
            <div class="services-text">
              <p>Smember</p>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import ClickOutside from 'vue-click-outside'
import locationSelect from './partials/locationSelect.vue'

export default {
  directives: {
    ClickOutside,
  },
  components: { locationSelect },
  data() {
    return {
      isInput: false,
    }
  },
  methods: {
    toggleShow() {
      this.isInput = true
    },
    hide() {
      this.isInput = false
    },
  },
}
</script>

<style lang="scss">
@import url('//maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css');

.background {
  position: fixed;
  visibility: hidden;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  z-index: 1;
  background: rgba(0, 0, 0, 0.7);
}
.background.active {
  z-index: 3;
  visibility: visible;
}

.header {
  visibility: visible;
  position: relative;
  width: 100%;
  background-color: #d70018;
  .header-container {
    position: relative;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
    width: 65%;
    margin: 0 auto 0;

    height: 64px;
    .header-icon {
      height: 1.9em;
      margin-right: 0.8em;
    }
    .header-logo {
      height: 1.9em;
      margin-right: 0.8em;

      img {
        height: 2em;
      }
    }
    .header-input {
      position: relative;
      color: #aaa;
      margin: 0 1.5em 0;
      input {
        width: 22em;
        height: 2.5em;
        text-indent: 2.2em;
        font-size: 14px;
        background: #fcfcfc;
        border: none;
        border-radius: 8px;
        box-shadow: 0 0 3px #ccc, 0 10px 15px #ebebeb inset;
        &:focus {
          outline: none !important;
        }
      }
      .fa-search {
        position: absolute;
        color: #707070;
        top: 0.5em;
        left: 0.5em;
      }
    }
    .services {
      display: flex;
      list-style-type: none;
      justify-content: space-around;
      position: relative;
      .services-phone {
        display: flex;
        width: 8em;
        height: 2.5em;
        justify-content: center;
        align-items: center;
        border-radius: 8px;
        margin-left: 0.5em;
        cursor: pointer;
        &:hover {
          margin-left: 0.5em;
          background-color: #df3346;
        }
        .services-icon {
          height: 1.6em;
          width: 1.6em;
        }
        .services-text {
          display: flex;
          justify-content: center;
          text-align: left;
          font-size: 14px;
          line-height: 1.2;
          color: #fadde0;
          width: 100%;
          margin-left: 0.5em;
        }
      }
      .services-close {
        display: flex;
        width: 6.5em;
        height: 2.5em;
        justify-content: center;
        align-items: center;
        border-radius: 8px;
        margin-left: 0.5em;
        cursor: pointer;
        &:hover {
          background-color: #df3346;
        }
        .services-icon {
          height: 1.7em;
          width: 1.7em;
        }
        .services-text {
          display: flex;
          justify-content: left;
          text-align: left;
          font-size: 13px;
          line-height: 1.2;
          color: #fadde0;
          width: 100%;
          margin-left: 0.4em;
        }
      }
      .services-delivery {
        display: flex;
        width: 6.5em;
        height: 2.5em;
        justify-content: center;
        align-items: center;
        border-radius: 8px;
        margin-left: 0.5em;
        cursor: pointer;
        &:hover {
          background-color: #df3346;
        }
        .services-icon {
          height: 2.5em;
          width: 2.5em;
        }
        .services-text {
          display: flex;
          justify-content: left;
          text-align: left;
          font-size: 13px;
          line-height: 1.2;
          font-size: 500;
          color: #fadde0;
          width: 100%;
          margin-left: 0.4em;
        }
      }
      .services-cart {
        display: flex;
        width: 5em;
        height: 2.5em;
        justify-content: center;
        align-items: center;
        border-radius: 8px;
        margin-left: 1em;
        cursor: pointer;
        &:hover {
          background-color: #df3346;
        }
        .services-icon {
          height: 1.7em;
          width: 1.7em;
        }
        .services-text {
          display: flex;
          justify-content: left;
          text-align: left;
          font-size: 13px;
          line-height: 1.2;
          font-size: 500;
          color: #fadde0;
          width: 100%;
          margin-left: 0.4em;
        }
      }
      .services-login {
        display: flex;
        width: 4em;
        height: 2.5em;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        border-radius: 8px;
        cursor: pointer;
        &:hover {
          background-color: #df3346;
        }
        .services-icon {
          height: 1.4em;
          width: 1.4em;
        }
        .services-text {
          display: flex;
          justify-content: center;
          text-align: center;
          font-size: 13px;
          line-height: 1.2;
          font-size: 500;
          color: #fadde0;
          width: 100%;
          margin-left: 0.4em;
        }
      }
    }
  }
}
@media screen and (max-width: 560px) {
  .background {
    display: block;
    position: fixed;
    z-index: 3;
  }
  .header {
    display: block;
    background: linear-gradient(
      0deg,
      rgba(238, 144, 147, 1) 0%,
      rgba(222, 31, 51, 1) 100%
    );

    .header-container {
      position: relative;
      z-index: 1;
      width: 95%;
      height: 6.7em;
      justify-content: flex-start;
      align-items: flex-start;
      text-align: center;
      padding-top: 0.5em;
      .header-logo {
        height: 1.5em;
        margin: 0 1em 0 0.5em;
      }
      .header-icon {
        display: none;
      }
      .services {
        .services-close {
          display: none;
        }
        .services-phone {
          display: none;
        }
        .services-delivery {
          display: none;
        }
        .services-login {
          display: none;
        }
        .services-cart {
          display: block;
          margin-left: 0;
          margin-right: 0.5em;
          width: 3em;
          background-color: #ea6571;
          border-radius: 8px;
          .services-icon {
            height: 0.6em;
            width: 0.6em;
          }
          .services-text {
            font-size: 9px;
            font-weight: 700;
            margin-top: 0.3em;
          }
        }
      }
      .header-input {
        z-index: 1;
        margin: 0;
        width: 95vw;
        display: block;
        position: absolute;
        top: 3.5em;
        .fa-search {
          position: absolute;
          color: #707070;
          top: 0.5em;
          left: 1em;
        }
        input {
          width: 92vw;
          z-index: -1;
        }
      }
    }
  }
}
</style>
