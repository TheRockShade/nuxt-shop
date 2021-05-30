<template>
  <section class="catalog">
    <div class="catalog__inner container">
      <div v-if="page !== 'index'" class="catalog__top">
        <h2 class="catalog__header">Каталог</h2>
        <button class="catalog__btn" @click="toggleSort">
          <span class="catalog__btn-text">Сортировать</span>
          <span
            class="catalog__sort-item collection-order__icon icon-order"
          ></span>
        </button>
        <ul class="catalog__sort">
          <li class="catalog__sort-item">
            <button class="catalog__sort-btn">По умолчанию</button>
          </li>
          <li class="catalog__sort-item">
            <button class="catalog__sort-btn">По возрастанию цены</button>
          </li>
          <li class="catalog__sort-item">
            <button class="catalog__sort-btn">По убыванию цены</button>
          </li>
        </ul>
      </div>
      <Cards />
      <nuxt-link v-if="page === 'index'" class="catalog__all" to="/catalog">
        <span class="catalog__all-text">Смотреть всё</span>
        <span class="catalog__all-btn icon icon-angle-right"></span>
      </nuxt-link>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    page: {
      type: String,
      default: 'index',
    },
  },
  methods: {
    toggleSort() {
      document.querySelector('.catalog__sort').classList.toggle('open')
    },
  },
}
</script>

<style lang="scss" scoped>
.catalog {
  padding: 60px 0;

  &__top {
    position: relative;

    max-width: 750px;
    margin: 0 auto 20px auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__header {
    font-size: 24px;
  }

  &__btn {
    display: flex;
    align-items: center;

    background: transparent;

    &-text {
      margin-right: 5px;
    }

    &-item {
      font-size: 20px;
    }
  }

  &__sort {
    position: absolute;
    top: 45px;
    right: 0;

    width: 170px;
    display: none;
    flex-direction: column;
    z-index: 50;

    border-radius: 4px;
    box-shadow: 0 0 10px rgb(0 0 0 / 7%);

    &.open {
      display: flex;
    }

    &-btn {
      width: 100%;
      padding: 10px;

      font-size: 14px;
      text-align: left;

      background: #fff;

      &:hover {
        background: lightgray;
      }
    }
  }

  &__all {
    width: fit-content;
    margin: 40px auto 0 auto;
    display: flex;
    align-items: center;

    font-size: 18px;

    transition: opacity 0.3s ease;

    &-text {
      margin-right: 5px;
    }

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
