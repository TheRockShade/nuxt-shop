<template>
  <nuxt-link v-if="$route.name !== 'index'" class="logo" :class="mod" to="/">
    <img class="logo__item" :class="`${mod}-item`" src="logo.svg" alt="logo" />
  </nuxt-link>
  <img v-else class="logo__item" :class="mod" src="logo.svg" alt="logo" />
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
.logo__item {
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

  pointer-events: none;
}
</style>
