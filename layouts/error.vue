<template>
  <section class="error">
    <div class="error__inner grid-block">
      <h1 class="error__title">Oooops...</h1>
      <p class="error__text">Sorry, page not found :(</p>
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
