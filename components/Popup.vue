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
      <button class="popup__close" @click="popupClose">Х</button>
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

    padding: 50px;
    display: flex;
    justify-content: space-between;
    align-items: start;

    background: #fff;
    border: 2px solid black;
  }

  &.open {
    display: flex;
  }

  &__img {
    width: 500px;
  }

  &__info {
    max-width: 500px;
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
}
</style>
