<template>
  <section class="order">
    <div class="order__inner container">
      <h2 class="order__title">Оформление заказа</h2>
      <div class="order__price">
        <span class="order__price-text">Итого:</span>
        <span class="order__price-sum">{{ totalPrice }} ₽</span>
      </div>
      <form action="POST" class="order__form order-form">
        <h3 class="order-form__title">Контактные данные</h3>
        <label class="order-form__label">
          <span class="order-form__label-text"
            >Контактное лицо (ФИО)<span class="order-form__label-red">*</span>
          </span>
          <input class="order-form__input" name="name" type="text" />
        </label>
        <label class="order-form__label">
          <span class="order-form__label-text"
            >Контактный телефон<span class="order-form__label-red">*</span>
          </span>
          <input class="order-form__input" name="tel" type="text" />
        </label>
        <h3 class="order-form__title">Доставка</h3>
        <label class="order-form__label">
          <span class="order-form__label-text"
            >Населенный пункт<span class="order-form__label-red">*</span>
          </span>
          <input class="order-form__input" name="city" type="text" />
        </label>
        <label class="order-form__label">
          <span class="order-form__label-text">Комментарии к заказу</span>
          <textarea class="order-form__text" name="comment" rows="5"></textarea>
        </label>
      </form>
      <h3 class="order-form__title">Покупатель</h3>
      <label class="order-form__label">
        <span class="order-form__label-text">Email</span>
        <input class="order-form__input" name="email" type="email" />
      </label>
      <nuxt-link class="order-form__button" to="/thanks" @click="deleteCart"
        >Подтвердить заказ</nuxt-link
      >
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
    ...mapActions(['DELETE_CART']),
    deleteCart() {
      this.DELETE_CART()
    },
  },
}
</script>

<style lang="scss" scoped>
.order {
  max-width: 768px;
  margin: 0 auto;
  padding: 20px 0;
  box-sizing: border-box;

  &__title {
    font-size: 34px;
    font-weight: 700;

    margin-bottom: 16px;
  }

  &__price {
    margin-bottom: 20px;
    padding: 16px 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;

    background: #e6e6e6;

    &-text {
      font-size: 21px;
    }

    &-sum {
      font-size: 28px;
      font-weight: 700;
    }
  }

  &-form {
    &__title {
      margin-bottom: 16px;

      font-size: 28px;
    }

    &__label {
      margin-bottom: 16px;
      display: flex;
      flex-direction: column;

      &-text {
        margin-bottom: 8px;
      }

      &-red {
        margin-left: 5px;

        color: red;
      }
    }

    &__input,
    &__text {
      padding: 7px 10px;

      color: #333;

      border: 1px solid #808080;
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
}
</style>
