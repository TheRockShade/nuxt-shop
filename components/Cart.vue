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
      <h3 v-else class="cart__none">Ваша корзина пуста</h3>
    </div>
  </section>
</template>

<script>
import { mapGetters, mapActions } from 'vuex'
export default {
  computed: {
    ...mapGetters(['CART']),
  },
  methods: {
    ...mapActions(['ADD_TO_CART', 'DELETE_FROM_CART']),
    deleteFromCart(i) {
      this.DELETE_FROM_CART(i)
    },
  },
}
</script>
