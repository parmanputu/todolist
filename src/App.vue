<template>
  <AppHeader title="Test" />

  <main>{{ mainText }}</main>
</template>

<script>
import AppHeader from './components/AppHeader.vue'

export default {
  name: 'App',
  components: {
    AppHeader
  },
  data() {
    return {
      mainText: 'This is main text'
    }
  }
}
</script>

<style>
header {
  line-height: 1.5;
  background-color: aqua;
}
main {
  background-color: aquamarine;
}
</style>
