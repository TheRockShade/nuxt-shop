<template>
  <section class="catalog">
    <Popup v-if="item.brand" :data="item" @popupClose="closePopup" />
    <div class="catalog__inner container">
      <div v-if="$route.name !== 'index'" class="catalog__top">
        <h2 class="catalog__header">Каталог</h2>
        <button class="catalog__btn" @click="toggleSelect">
          <span class="catalog__btn-text">{{ selectedTitle }}</span>
          <span
            class="catalog__sort-item collection-order__icon icon-order"
          ></span>
        </button>
        <Select :options="sort" @select="optionSelect" />
      </div>
      <Cards :sort="selectedType" @good="getData" />
      <nuxt-link
        v-if="$route.name === 'index'"
        class="catalog__all"
        to="/catalog"
      >
        <span class="catalog__all-text">Смотреть всё</span>
        <span class="catalog__all-btn icon icon-angle-right"></span>
      </nuxt-link>
    </div>
  </section>
</template>

<script>
export default {
  props: {
    page: {
      type: String,
      default: 'index',
    },
  },
  data() {
    return {
      sort: [
        { name: 'По умолчанию', value: 'default' },
        { name: 'По возрастанию цены', value: 'price up' },
        { name: 'По убыванию цены', value: 'price down' },
      ],
      selected: '',
      selectedType: '',
      selectedTitle: 'Сортировать',
      item: {},
    }
  },
  methods: {
    toggleSelect() {
      document.querySelector('.select').classList.toggle('open')
    },
    optionSelect(option) {
      this.selected = option.name
      this.selectedType = option.value
      this.selectedTitle = option.name
      this.toggleSelect()
    },
    getData(data) {
      this.item = data
    },
    closePopup() {
      this.item = {}
    },
  },
}
</script>

<style lang="scss" scoped>
.catalog {
  padding: 60px 0;

  &__top {
    position: relative;

    max-width: 750px;
    margin: 0 auto 20px auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
  }

  &__header {
    font-size: 24px;
  }

  &__btn {
    display: flex;
    align-items: center;

    background: transparent;

    &-text {
      margin-right: 5px;
    }

    &-item {
      font-size: 20px;
    }
  }

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
