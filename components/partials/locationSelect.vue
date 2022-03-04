<template>
  <div class="loca__container">
    <div class="loca__active">
      <div v-click-outside="hide" class="loca__title" @click="toggleShow">
        <img src="@/assets/images/loca.svg" class="loca__icon" />
        <div class="loca__title--text">
          <p>Xem giá tại</p>
          <p class="loca__label">
            {{ locations[active].location }}
            <i class="fa fa-chevron-down fa-xs"></i>
          </p>
        </div>
      </div>
      <div v-if="showMenu" class="select__child">
        <ul>
          <li
            v-for="(location, index) in locations"
            :key="index"
            class="enabled locachild__li"
            @click.prevent="changeLang(index)"
          >
            <img src="@/assets/images/pin.png" class="loca__pin" />
            <span class="locachild__li--text">{{ location.location }} </span>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import ClickOutside from 'vue-click-outside'
export default {
  directives: {
    ClickOutside,
  },
  data() {
    return {
      showMenu: false,
      locations: [
        {
          location: 'Miền Nam',
        },
        {
          location: 'Miền Bắc',
        },
      ],
      active: 1,
    }
  },
  methods: {
    toggleShow() {
      this.showMenu = !this.showMenu
    },
    hide() {
      this.showMenu = false
    },
    changeLang(index) {
      this.active = index
    },
  },
}
</script>

<style lang="scss" scoped>
.loca__container {
  position: relative;
  display: flex;
  background-color: #df3346;
  width: 8em;
  height: 2.5em;
  justify-content: center;
  align-items: center;
  border-radius: 8px;
  .loca__active {
    width: 100%;
    .loca__title {
      cursor: pointer;
      display: flex;
      flex-direction: row;
      .loca__icon {
        height: 1em;
        width: 1.5em;
        margin-top: auto;
        margin-bottom: auto;
      }
      .loca__title--text {
        display: flex;
        justify-content: center;
        align-items: left;
        text-align: left;
        font-size: 10px;
        color: #fadde0;
        flex-direction: column;
        width: 100%;
        margin-left: 0.5em;
        .loca__label {
          font-size: 12px;
          font-weight: 700;
          line-height: 22px;
          width: 70%;
          letter-spacing: 0.325px;
          .fa-chevron-down {
            font-size: 8px;
          }
        }
      }
    }
    .select__child {
      z-index: 3;
      border-radius: 8px;
      position: absolute;
      visibility: visible;
      background-color: #ffffff;
      width: 9.5em;
      height: 3.7em;
      top: 3em;
      ul {
        height: 100%;

        .locachild__li {
          list-style-type: none;
          height: 50%;
          display: flex;
          justify-content: left;
          align-items: center;
          cursor: pointer;
          font-size: 14px;
          .loca__pin {
            width: 0.8em;
            height: 0.8em;
            margin-left: 1.3em;
            margin-right: 0.5em;
          }
          &:hover {
            background-color: #fee2e2;
            border-radius: 8px;
          }
        }
      }
    }
  }
}
@media only screen and (max-width: 560px) {
  .loca__container {
    width: 100%;
    margin-right: 1.5em;
    .loca__active {
      .loca__title {
        height: 2.5em;
        width: 100%;
        background-color: #ea6571;
        border-radius: 8px;
        .loca__icon {
          width: 0.7em;
          height: 0.7em;
          margin-left: 0.5em;
        }
        .loca__title--text {
          p {
            font-size: 8px;
            font-weight: 500;
          }
          .loca__label {
            font-size: 9px;
            line-height: 20px;
            font-weight: 700;
            .fa-chevron-down {
              position: absolute;
              right: 2.7em;
              bottom: 1.7em;
              font-size: 7px;
            }
          }
        }
      }
      .select__child {
        width: 10em;
        height: 3em;
        top: 2.7em;
        .locachild__li--text {
          font-size: 14px;
        }
        ul .locachild__li {
          .loca__pin {
            width: 1em;
            height: 1em;
            margin-left: 1.3em;
            margin-right: 0.5em;
          }
        }
      }
    }
  }
}
@media only screen and (max-width: 400px) {
  .loca__container {
    margin-right: 0.5em;
    .loca__active {
      .loca__title {
        .loca__icon {
          width: 0.7em;
          height: 0.7em;
          margin-left: 0.5em;
        }
        .loca__title--text {
          font-size: 7px;
          .loca__label {
            font-size: 7px;
            line-height: 20px;
            font-weight: 700;
            .fa-chevron-down {
              position: absolute;
              right: 1em;
              bottom: 1.7em;
              font-size: 7px;
            }
          }
        }
      }
      .select__child {
        width: 10em;
        height: 3em;
        top: 2.7em;
        .locachild__li--text {
          font-size: 14px;
        }
        ul .locachild__li {
          .loca__pin {
            width: 1em;
            height: 1em;
            margin-left: 1.3em;
            margin-right: 0.5em;
          }
        }
      }
    }
  }
}
</style>
