<template>
  <ul class="select">
    <li v-for="option in options" :key="option.value" class="select__item">
      <button class="select__btn" @click="selectOption(option)">
        {{ option.name }}
      </button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    options: {
      type: Array,
      default() {
        return []
      },
    },
  },
  methods: {
    selectOption(option) {
      this.$emit('select', option)
    },
  },
}
</script>

<style lang="scss" scoped>
.select {
  position: absolute;
  top: 45px;
  right: 0;

  width: 170px;
  display: none;
  flex-direction: column;
  z-index: 50;

  border-radius: 4px;
  box-shadow: 0 0 10px rgb(0 0 0 / 7%);

  &.open {
    display: flex;
  }

  &__btn {
    width: 100%;
    padding: 10px;

    font-size: 14px;
    text-align: left;

    background: #fff;

    &:hover {
      background: lightgray;
    }
  }
}
</style>
