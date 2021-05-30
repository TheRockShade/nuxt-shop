<template>
  <div class="menu">
    <h3 class="menu__header">Меню</h3>
    <nav class="menu__nav">
      <ul class="menu__list">
        <li
          v-for="item of menu"
          :key="item.length"
          class="menu__item"
          @click="toggleMenu"
        >
          <nuxt-link class="menu__link" :to="item.link">{{
            item.name
          }}</nuxt-link>
        </li>
      </ul>
    </nav>
    <h3 class="menu__header">Контакты</h3>
    <ul class="menu__contacts">
      <li class="menu__contacts-item">8 800 555 35 35</li>
      <li class="menu__contacts-item">г. Тольятти, Степана Разина пр., 44</li>
    </ul>
    <Social class="menu__social" />
    <button class="menu__close" @click="toggleMenu">
      <span class="menu__close-item icon icon-times"></span>
    </button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menu: [
        { name: 'Каталог', link: '/catalog' },
        { name: 'О компании', link: '/about' },
        { name: 'Контакты', link: '/contacts' },
        { name: 'Доставка', link: '/delivery' },
        // { name: 'Личный кабинет', link: '/user' },
      ],
    }
  },
  methods: {
    toggleMenu() {
      document.querySelector('body').classList.toggle('bg')
      document.querySelector('.menu').classList.toggle('open')
    },
  },
}
</script>

<style lang="scss" scoped>
.menu {
  position: absolute;
  top: 0;
  left: 0;

  width: 500px;
  height: 100vh;
  padding: 32px;
  transform: translateX(-550px);
  z-index: 100;
  pointer-events: initial;

  background: #fff;

  transition: transform 0.4s ease;

  @include media_interval(0, $media768) {
    height: 100vh;
    width: 100vw;
    transform: translateX(-200vw);
  }

  &.open {
    transform: translate(0);
  }

  &__header {
    margin-bottom: 13px;

    font-weight: 700;
  }

  &__nav {
    margin-bottom: 24px;
    padding-bottom: 24px;

    border-bottom: 1px solid #f7f7f7;
  }

  &__list {
    width: 100%;
  }

  &__item {
    &:not(:last-child) {
      margin-bottom: 13px;
    }
  }

  &__link {
    &:hover {
      text-decoration: underline;
    }
  }

  &__contacts {
    margin-bottom: 24px;
    padding-bottom: 24px;

    border-bottom: 1px solid #f7f7f7;
    &-item {
      &:not(:last-child) {
        margin-bottom: 13px;
      }
    }
  }

  &__close {
    position: absolute;
    top: 24px;
    right: -50px;

    width: 40px;
    height: 40px;

    background: #fff;
    border-radius: 50%;

    @include media_interval(0, $media768) {
      width: 20px;
      height: 20px;
      right: 32px;
    }
  }
}
</style>
