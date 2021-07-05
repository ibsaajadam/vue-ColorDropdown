<template>
  <div id="app">
    <Color />
  </div>
</template>

<script>
import Color from './components/Color.vue'

export default {
  name: 'App',
  components: {
    Color
  }
}
</script>

<style lang="scss">
@import '../src/scss/main.scss';
</style>
