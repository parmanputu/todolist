<template>
  <HeaderTitle title="Test" />

  <main>{{ mainText }}</main>
</template>

<script>
import HeaderTitle from './components/HeaderTitle.vue'

export default {
  name: 'App',
  components: {
    HeaderTitle
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
