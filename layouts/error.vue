<template>
  <section class="error">
    <div class="error__inner container">
      <h1 class="error__title">Упс...</h1>
      <p class="error__text">Страницы не существует</p>
      <nuxt-link class="error__link" to="/">На главную</nuxt-link>
    </div>
  </section>
</template>

<script>
export default {
  layout: 'add',
  head() {
    return {
      title: '404',
    }
  },
}
</script>

<style lang="scss" scoped>
.error {
  padding: 30vh 0 190px 0;
  &__inner {
    display: flex;
    flex-direction: column;
    align-items: center;
  }

  &__title {
    margin-bottom: 20px;

    font-size: 60px;
    font-weight: 500;
  }

  &__text {
    margin-bottom: 20px;

    font-size: 24px;
  }

  &__link {
    font-size: 24px;
    text-decoration: underline;

    &:hover {
      text-decoration: none;
    }
  }
}
</style>
