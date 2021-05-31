<template>
  <section class="cart">
    <div class="cart__inner container">
      <h2 class="cart__title">Корзина</h2>
      <ul v-if="CART.length" class="cart__list">
        <CartItem
          v-for="(item, i) in CART"
          :key="item.length"
          :info="item"
          @deleteFromCart="deleteFromCart(i)"
        />
      </ul>
      <div v-if="CART.length" class="cart__order">
        <div class="cart__total">
          <span class="cart__total-text">Итого к оплате:</span>
          <span class="cart__total-price">{{ totalPrice }} ₽</span>
        </div>
        <nuxt-link class="cart__button" to="/order">Оформить заказ</nuxt-link>
      </div>
      <h3 v-else class="cart__none">Ваша корзина пуста</h3>
    </div>
  </section>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  computed: {
    ...mapGetters(['CART']),
    totalPrice() {
      let sum = 0
      this.CART.forEach((el) => {
        sum += el.price
      })
      return sum
    },
  },
  methods: {
    ...mapActions(['ADD_TO_CART', 'DELETE_FROM_CART']),
    deleteFromCart(i) {
      this.DELETE_FROM_CART(i)
    },
  },
}
</script>

<style lang="scss" scoped>
.cart {
  padding: 15px 0;
  &__title {
    margin-bottom: 20px;

    font-size: 24px;

    @include media_interval(0, $media600) {
      font-size: 18px;
    }
  }

  &__order {
    max-width: 600px;
    margin: 0 auto;

    background: #f7f7f7;
  }

  &__total {
    padding: 24px;
    display: flex;
    justify-content: space-between;

    font-size: 18px;
    &-text {
      font-weight: normal;
    }
  }

  &__button {
    width: 100%;
    padding: 20px;
    display: block;

    font-size: 20px;
    text-align: center;
    color: #fff;

    background: #1b2738;
  }
}
</style>
