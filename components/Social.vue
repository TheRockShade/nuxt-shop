<template>
  <ul class="social">
    <li v-for="social in socials" :key="social.length" class="social__item">
      <a class="social__link" :href="`https://${social.link}`" target="_blank">
        <img
          class="social__img"
          :src="`social-${social.name}.svg`"
          :alt="social.name"
        />
      </a>
    </li>
  </ul>
</template>

<script>
export default {
  data() {
    return {
      socials: [
        { name: 'facebook', link: 'facebook.com' },
        { name: 'instagram', link: 'instagram.com' },
        { name: 'telegram', link: 'telegram.com' },
        { name: 'twitter', link: 'twitter.com' },
        { name: 'vk', link: 'vk.com' },
        { name: 'youtube', link: 'youtube.com' },
      ],
    }
  },
}
</script>

<style lang="scss" scoped>
.social {
  display: flex;
  align-items: center;

  &__item {
    &:not(:last-child) {
      margin-right: 15px;
    }
  }
}
</style>
