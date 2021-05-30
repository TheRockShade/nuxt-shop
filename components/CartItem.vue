<template>
  <li class="cart__item">
    <img class="cart__img" :src="imgPath(info)" />
    <h3 class="cart__header">{{ info.brand + ' ' + info.model }}</h3>
    <span class="cart__price">{{ info.price }} ₽</span>
    <button class="cart__delete" @click="deleteFromCart">Delete</button>
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
  &__img {
    width: 100px;
  }

  &__delete {
    padding: 10px;
    display: block;
  }
}
</style>
