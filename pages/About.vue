<template>
  <section class="about">
    <div class="about__inner container">
      <h2 class="about__title">О компании</h2>
      <p class="about__text about__text--bold">
        Интернет-магазин "Mono.ru" – лучшие смартфоны по низким ценам!
      </p>
      <p class="about__text">
        Мы рады предложить вам недорогие, но качественные товары с подробными
        описаниями, характеристиками и фотографиями. У нас Вы можете купить
        замечательные товары: технику, электронику, одежду, обувь, игрушки,
        книги и многое другое в вашем регионе по ценам производителей и без
        наценки.
      </p>
      <p class="about__text about__text--bold">Наши главные преимущества:</p>
      <ul class="about__list">
        <li class="about__item">Низкие цены от производителей</li>
        <li class="about__item">Доставка по городу в день заказа</li>
        <li class="about__item">
          Доставка заказов Почтой по всей Стране за 5-15 дней
        </li>
      </ul>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.about {
  padding: 60px 0;
  &__title {
    margin-bottom: 16px;

    font-size: 24px;
  }

  &__text {
    margin-bottom: 16px;

    &--bold {
      font-weight: 700;
    }
  }

  &__list {
    margin-left: 20px;

    list-style: initial;
  }

  &__item {
    &:not(:last-child) {
      margin-bottom: 10px;
    }
  }
}
</style>
