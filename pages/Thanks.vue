<template>
  <section class="thanks">
    <div class="thanks__inner container">
      <h1 class="thanks__title">Спасибо за заказ!</h1>
      <nuxt-link class="thanks__link" to="/">На главную</nuxt-link>
    </div>
  </section>
</template>

<script>
export default {
  layout: 'add',
  head() {
    return {
      title: 'Mono | Спасибо!',
    }
  },
}
</script>

<style lang="scss" scoped>
.thanks {
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

  &__link {
    font-size: 24px;
    text-decoration: underline;

    &:hover {
      text-decoration: none;
    }
  }
}
</style>
