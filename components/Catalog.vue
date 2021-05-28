<template>
  <section class="catalog">
    <div class="catalog__inner container">
      <Cards />
      <nuxt-link class="catalog__all" to="/catalog">
        <span class="catalog__all-text">Смотреть всё</span>
        <span class="catalog__all-btn icon icon-angle-right"></span>
      </nuxt-link>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.catalog {
  padding: 60px 0;

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
