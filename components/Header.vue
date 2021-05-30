<template>
  <header class="header">
    <div class="header__inner container">
      <button class="header__button" @click="toggleMenu">
        <span class="header__button-icon icon icon-bars"></span>
        <span class="header__button-text">Меню</span>
      </button>
      <Logo mod="header__logo" />
      <ul class="header__bar">
        <li class="header__bar-item">
          <nuxt-link class="header__bar-link" to="/favorites">
            <span class="icon icon-favorites"></span>
          </nuxt-link>
        </li>
        <li class="header__bar-item">
          <nuxt-link class="header__bar-link" to="/basket">
            <span class="icon icon-cart"></span>
          </nuxt-link>
        </li>
      </ul>
    </div>
  </header>
</template>

<script>
export default {
  methods: {
    toggleMenu() {
      document.querySelector('body').classList.toggle('bg')
      document.querySelector('.menu').classList.toggle('open')
    },
  },
}
</script>

<style lang="scss" scoped>
.header {
  padding: 14px 0;

  &__inner {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  &__button {
    display: flex;
    align-items: center;

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

    &-icon {
      font-size: 22.4px;
      margin-right: 10px;
    }

    &-text {
      font-weight: 700;

      @include media_interval(0, $media768) {
        font-size: 0;
      }
    }
  }

  &__bar {
    display: flex;
    &-item {
      font-size: 24px;

      &:not(:last-child) {
        margin-right: 15px;
      }
    }

    &-link {
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
}
</style>
