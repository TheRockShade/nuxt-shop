<template>
  <ul class="cards">
    <li v-for="good in goodsArr()" :key="good.id" class="cards__item">
      <img class="cards__img" :src="imgPath(good)" />
      <h6 class="cards__title">{{ good.brand + ' ' + good.model }}</h6>
      <div class="cards__bottom">
        <span class="cards__price">{{ good.price }} ₽</span>
        <button
          class="cards__btn cards__btn--basket icon icon-cart"
          @click="addToCart(good)"
        ></button>
      </div>
    </li>
  </ul>
</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
  data() {
    return {}
  },
  computed: {
    ...mapGetters(['PRODUCTS']),
  },
  mounted() {
    this.GET_PRODUCTS_FROM_API()
  },
  methods: {
    ...mapActions(['GET_PRODUCTS_FROM_API', 'ADD_TO_CART']),
    imgPath(item) {
      return `${(item.brand + '-' + item.model)
        .replace(/ /g, '-')
        .toLowerCase()}.png`
    },
    addToCart(data) {
      this.ADD_TO_CART(data)
    },
    goodsArr() {
      if (this.$route.name === 'index') {
        return this.PRODUCTS.slice(0, 4)
      }
      return this.PRODUCTS
    },
  },
}
</script>

<style lang="scss" scoped>
.cards {
  max-width: 750px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;

  &__item {
    position: relative;

    @include media_interval($media768, 0) {
      @include flex-columns(4, 30px, 30px);
    }

    @include media_interval($media600, $media768) {
      @include flex-columns(3, 30px, 30px);
    }

    @include media_interval(0, $media600) {
      @include flex-columns(2, 30px, 30px);
    }
  }

  &__img {
    margin-bottom: 8px;
  }

  &__title {
    margin-bottom: 15px;

    font-size: 16px;
    font-weight: 400;
  }

  &__bottom {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__price {
    font-size: 16px;
    font-weight: 500;
  }

  &__btn {
    padding: 0;

    font-size: 24px;

    background: transparent;
    border: none;
    cursor: pointer;

    transition: opacity 0.3s ease;

    &:hover,
    &:focus {
      opacity: 0.7;
    }

    &:active {
      opacity: 0.5;
    }
  }
}
</style>
