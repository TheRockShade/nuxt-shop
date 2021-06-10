<template>
  <div class="popup">
    <div class="popup__inner">
      <img v-if="data.brand" :src="imgPath(data)" class="popup__img" />
      <div class="popup__info">
        <h3 class="popup__title">{{ data.brand + ' ' + data.model }}</h3>
        <span class="popup__price">{{ data.price }} ₽</span>
        <button class="popup__button" @click="addToCart(data)">
          В корзину
        </button>
        <p class="popup__desc">{{ data.description }}</p>
      </div>
      <button class="popup__close" @click="popupClose">
        <span class="popup__close-item icon icon-times"></span>
      </button>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  props: {
    data: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    ...mapActions(['ADD_TO_CART']),
    imgPath(item) {
      return `${(item.brand + '-' + item.model)
        .replace(/ /g, '-')
        .toLowerCase()}.png`
    },
    popupClose() {
      this.$emit('popupClose')
    },
    addToCart(data) {
      this.ADD_TO_CART(data)
    },
  },
}
</script>

<style lang="scss" scoped>
.popup {
  position: fixed;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;

  z-index: 100;

  background: rgba(#000, 0.2);
  &__inner {
    position: absolute;
    top: 100px;
    bottom: 100px;
    left: 100px;
    right: 100px;
    overflow: scroll;

    padding: 50px;
    display: flex;
    justify-content: space-between;
    align-items: start;

    background: #fff;
    border: 2px solid black;

    @include media_interval(0, $media768) {
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;

      padding: 20px;
      flex-direction: column;
      align-items: center;
      justify-content: flex-start;
    }
  }

  &.open {
    display: flex;
  }

  &__img {
    width: 500px;

    @include media_interval(0, $media768) {
      width: 80%;
      margin-bottom: 20px;
    }
  }

  &__info {
    max-width: 500px;

    @include media_interval(0, $media768) {
      width: 100%;
      max-width: 100%;
    }
  }

  &__title {
    margin-bottom: 8px;

    font-size: 24px;
  }

  &__price {
    margin-bottom: 16px;
    display: block;

    font-size: 32px;
    font-weight: 700;
  }

  &__button {
    width: 100%;
    margin-bottom: 20px;
    padding: 20px;
    display: block;

    font-size: 20px;
    text-align: center;
    color: #fff;

    background: #1b2738;
  }

  &__close {
    position: absolute;
    top: 0;
    right: 0;

    width: 40px;
    height: 40px;

    background: #fff;
    border-radius: 50%;

    @include media_interval(0, $media768) {
      top: 10px;
      right: 10px;

      width: 20px;
      height: 20px;
    }
  }
}
</style>
