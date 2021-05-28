<template>
  <nuxt-link class="logo" :class="mod" to="/">
    <img class="logo__item" :class="`${mod}-item`" src="logo.svg" alt="logo" />
  </nuxt-link>
</template>

<script>
export default {
  props: {
    mod: {
      type: String,
      default: '',
    },
  },
}
</script>

<style lang="scss" scoped>
.logo {
  transition: opacity 0.3s ease;

  &:hover,
  &:focus {
    opacity: 0.7;
  }

  &:active {
    opacity: 0.5;
  }

  @include media_interval(0, $media768) {
    width: 120px;
    height: 27px;
  }

  &__item {
    pointer-events: none;
  }
}
</style>
