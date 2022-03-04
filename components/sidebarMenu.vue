<template>
  <div>
    <ul class="sidebar-container">
      <li
        v-for="(m, index) in items"
        :key="index"
        class="sidebar"
        :class="{ active: show === index }"
        @mouseover="show = index"
        @mouseout="show = false"
      >
        <img
          :src="require('@/assets/images' + m.icon)"
          alt="icon"
          class="sidebar-icon"
        />

        <span>{{ m.name }}</span>
        <i v-if="m.children" class="fa fa-chevron-right fa-xs"></i>
        <transition name="fade">
          <ul
            v-show="show === index"
            class="sidebar__selector"
            :class="{ empty: !m.children }"
          >
            <li
              v-for="(n, count) in items[index].children"
              :key="count"
              class="sidebar__selector--text"
            >
              <span>{{ n.name }}</span>
            </li>
          </ul>
        </transition>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  data() {
    return {
      show: false,
      items: [
        {
          name: 'Điện thoại',
          icon: '/phone.png',
          children: [
            {
              name: 'Apple',
              children: [
                {
                  lable: 'Iphone',
                },
              ],
            },
            {
              name: 'Samsung',
            },
            {
              name: 'Xiaomi',
            },
            {
              name: 'Oppo',
            },
            {
              name: 'Nokia',
            },
            {
              name: 'Realme',
            },
            {
              name: 'Vsmart',
            },
            {
              name: 'Asus',
            },
            {
              name: 'Vivo',
            },
            {
              name: 'Oneplus',
            },
            {
              name: 'Nobia',
            },
            {
              name: 'Cat',
            },
            {
              name: 'Điện thoại phổ thông',
            },
            {
              name: 'Techno',
            },
            {
              name: 'Hãng khác',
            },
          ],
        },
        {
          name: 'Laptop, PC, Màn hình',
          icon: '/laptop.png',
          children: [
            {
              name: 'Mac',
            },
            {
              name: 'HP',
            },
            {
              name: 'Dell',
            },
            {
              name: 'Lenovo',
            },
            {
              name: 'Surface',
            },
            {
              name: 'Asus',
            },
            {
              name: 'Acer',
            },
            {
              name: 'LG',
            },
            {
              name: 'Msi',
            },
            {
              name: 'Laptop Avita',
            },
            {
              name: 'Gibabyte',
            },
            {
              name: 'Máy in',
            },
            {
              name: 'Màn Hình',
            },
            {
              name: 'Linh kiện máy tính',
            },
          ],
        },
        {
          name: 'Tablet',
          icon: '/tablet.png',
          children: [
            {
              name: 'Ipad pro',
            },
            {
              name: 'Ipad 10.2',
            },
            {
              name: 'Ipad Air',
            },
            {
              name: 'Ipad mini',
            },
            {
              name: 'Samsung',
            },
            {
              name: 'Lenovo',
            },
            {
              name: 'Xiaomi',
            },
            {
              name: 'Kindle',
            },
            {
              name: 'Máy đọc sách',
            },
          ],
        },
        {
          name: 'Âm thanh',
          icon: '/earbuds.png',
          children: [
            {
              name: 'Loa',
            },
            {
              name: 'Tai nghe',
            },
            {
              name: 'Phụ kiện',
            },
            {
              name: 'Phòng thu âm',
            },
          ],
        },
        {
          name: 'Đồng hồ',
          icon: '/watch.png',
          children: [
            {
              name: 'Apple Watch',
            },
            {
              name: 'Samsung',
            },
            {
              name: 'Huewei',
            },
            {
              name: 'Xiaomi',
            },
            {
              name: 'Oppo',
            },
            {
              name: 'Hãng khác',
            },
            {
              name: 'Vòng tay thông minh',
            },
            {
              name: 'Coros',
            },
          ],
        },
        {
          name: 'Nhà thông minh',
          icon: '/smart-house.png',
          children: [
            {
              name: 'Máy hút bụi',
            },
            {
              name: 'Khóa thông minh',
            },
            {
              name: 'Đèn',
            },
            {
              name: 'Tv Box',
            },
            {
              name: 'Máy chạy bộ',
            },
            {
              name: 'Wifi Mesh',
            },
            {
              name: 'Camera an ninh',
            },
          ],
        },
        {
          name: 'Phụ kiện',
          icon: '/usb.png',
          children: [
            {
              name: 'Phụ kiện Apple',
            },
            {
              name: 'Dán điện thoại | laptop',
            },
            {
              name: 'Ốp lưng',
            },
            {
              name: 'Cáp sạc',
            },
            {
              name: 'Balo | túi xách',
            },
            {
              name: 'Pin dự phòng',
            },
            {
              name: 'Chuột | bàn phím',
            },
            {
              name: 'Thẻ nhớ, USB',
            },
          ],
        },
        {
          name: 'Thu cũ',
          icon: '/phone-2.png',
          children: [
            {
              name: 'Cellphones',
            },
            {
              name: 'SKtei',
            },
            {
              name: 'Compasia',
            },
          ],
        },
        {
          name: 'Hàng cũ',
          icon: '/mobile-payment.png',
          children: [
            {
              name: 'Máy tinh bảng',
            },
            {
              name: 'Laptop',
            },
            {
              name: 'Mac',
            },
            {
              name: 'Tai nghe',
            },
            {
              name: 'Đồng hồ thông minh',
            },
            {
              name: 'Phụ kiện',
            },
          ],
        },
        {
          name: 'Sim thẻ',
          icon: '/sim-card.png',
        },
        {
          name: 'Tin công nghệ',
          icon: '/newspaper.png',
        },
        {
          name: 'Khuyến mãi',
          icon: '/megaphone.png',
        },
      ],
    }
  },
}
</script>

<style lang="scss">
.sidebar-container {
  display: flex;
  flex-direction: column;
  list-style: none;
  width: 95%;
  border-radius: 1rem;
  box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
    rgb(60 64 67 / 15%) 0px 2px 6px 2px;
  .sidebar {
    display: block;
    width: 100%;
    justify-content: center;
    align-items: center;
    height: 2.7em;
    cursor: pointer;
    list-style: none;
    font-size: 12px;
    font-weight: 700;
    span {
      position: relative;
      bottom: 0.5em;
    }
    .sidebar-icon {
      position: relative;
      top: 0.2em;
      margin: 0 0.5em 0 1em;
    }
    .fa {
      position: relative;
      margin-right: 1em;
      top: 0.5em;
    }
    .fa-chevron-right {
      position: relative;
      float: right;
      font-weight: 100;
      top: 1em;
    }
    .sidebar__selector {
      visibility: hidden;
    }
    .sidebar__selector.empty {
      visibility: hidden !important;
    }
    &.active {
      &:hover {
        background-color: #f3f4f6;
        .sidebar__selector {
          visibility: visible;
        }
      }
      .sidebar__selector {
        list-style: none;
        z-index: 1000;
        position: absolute;
        display: flex;
        flex-direction: column;
        width: 20em;
        min-height: 32.4em;
        left: 18.69em;
        top: 0em;
        height: auto;
        // border-radius: 1rem;
        background-color: #ffffff;
        box-shadow: rgb(60 64 67 / 10%) 0px 1px 2px 0px,
          rgb(60 64 67 / 15%) 0px 2px 6px 2px;
        &--text {
          display: flex;
          justify-content: left;
          align-items: center;
          height: 2.7em;
          &:hover {
            background-color: #f3f4f6;
          }
          span {
            position: relative;
            margin-left: 1em;
            top: 0.1em;
          }
        }
      }
    }
  }
}

.fade-enter-active,
.fade-leave-active {
  transition: opacity 0.5s;
}

.fade-enter,
.fade-leave-to .fade-leave-active {
  opacity: 0;
}
</style>