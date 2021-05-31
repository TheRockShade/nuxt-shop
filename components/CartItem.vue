<template>
  <li class="cart__item">
    <nuxt-link :to="linkPath(info)">
      <img class="cart__img" :src="imgPath(info)" />
    </nuxt-link>
    <div class="cart__box">
      <nuxt-link class="cart__link" :to="linkPath(info)">
        <h3 class="cart__header">{{ info.brand + ' ' + info.model }}</h3>
      </nuxt-link>
      <span class="cart__price">{{ info.price }} ₽</span>
      <button
        class="cart__delete icon icon-trash"
        @click="deleteFromCart"
      ></button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    info: {
      type: Object,
      default() {
        return {}
      },
    },
  },
  methods: {
    imgPath(item) {
      return `${(item.brand + '-' + item.model)
        .replace(/ /g, '-')
        .toLowerCase()}.png`
    },
    linkPath(item) {
      return `catalog/${(item.brand + '-' + item.model)
        .replace(/ /g, '-')
        .toLowerCase()}`
    },
    deleteFromCart() {
      this.$emit('deleteFromCart')
    },
  },
}
</script>

<style lang="scss" scoped>
.cart {
  &__item {
    display: flex;
    margin-bottom: 20px;
  }

  &__link {
    margin-right: auto;

    @include media_interval(0, $media600) {
      margin-right: initial;
    }
  }

  &__img {
    width: 120px;
  }

  &__box {
    width: 100%;
    margin-top: 10px;
    display: flex;
    justify-content: flex-end;
    align-items: flex-start;

    @include media_interval(0, $media600) {
      flex-direction: column;
      justify-content: space-between;
      align-items: flex-end;
    }
  }

  &__header {
    font-size: 20px;

    @include media_interval(0, $media600) {
      font-size: 14px;
    }
  }

  &__price {
    margin-right: 30px;

    font-size: 22px;
    font-weight: 700;

    @include media_interval(0, $media600) {
      margin-right: 0;

      font-size: 18px;
    }
  }

  &__delete {
    padding: 3px;
    z-index: 10;

    background: transparent;
  }
}
</style>
