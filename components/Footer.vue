<template>
  <footer class="footer">
    <div class="footer__inner container">
      <ul class="footer__contacts">
        <li class="footer__contacts-item">8 800 555 35 35</li>
        <li class="footer__contacts-item">
          г. Тольятти, Степана Разина пр., 44
        </li>
      </ul>
      <Logo mod="footer__logo" />
      <Social />
    </div>
  </footer>
</template>

<style lang="scss" scoped>
.footer {
  padding: 60px 0;
  &__inner {
    display: flex;
    justify-content: space-between;
    align-items: center;

    @include media_interval(0, 900px) {
      flex-direction: column;
    }
  }

  &__contacts {
    &-item {
      @include font-size(18px);
      &:not(:last-child) {
        margin-bottom: 10px;
      }

      @include media_interval(0, 900px) {
        margin-bottom: 20px;

        text-align: center;
      }
    }
  }

  &__logo {
    @include media_interval(0, 900px) {
      margin-bottom: 20px;
    }
  }
}
</style>
