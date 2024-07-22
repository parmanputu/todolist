<template>
  <header>
    <h1 class="text-3xl font-bold underline mb-5">{{ title }}</h1>
  </header>
</template>

<script>
export default {
  name: 'AppHeader',
  props: {
    title: {
      type: String,
      required: true
    }
  }
}
</script>
