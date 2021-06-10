<template>
  <section class="about">
    <div class="about__inner container">
      <img class="about__icon" src="store.svg" alt="store" />
      <h4 class="about__title">О магазине Mono</h4>
      <p class="about__text">
        Mono - это современный, минималистичный, и удобный магазин смартфонов.
        Наша задача - это создать комфорт при выборе смартфона и его покупке.
      </p>
      <nuxt-link class="about__link" to="/about">Подробнее</nuxt-link>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.about {
  padding: 20px 0;

  &__inner {
    text-align: center;
  }

  &__icon {
    margin-bottom: 16px;
  }

  &__title {
    margin-bottom: 16px;
  }

  &__text {
    max-width: 750px;
    margin: 0 auto 16px auto;
  }

  &__link {
    text-decoration: underline;

    &:hover,
    &:focus {
      text-decoration: none;
    }
  }
}
</style>
