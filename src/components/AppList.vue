<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input type="text" name="inputTodo" v-model="inputTodo" />
      <button type="submit">Add Todo</button>
    </form>
  </div>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <input
        type="checkbox"
        name="checkTodo"
        :checked="todo.status === 'done'"
        @change="toggle(todo.id)"
      />
      {{ todo.name }}
    </li>
  </ul>
</template>

<script>
export default {
  name: 'AppList',
  props: {
    todos: {
      type: Array,
      required: true
    }
  },
  emits: ['add-todo', 'toggle-todo'],
  data() {
    return {
      inputTodo: ''
    }
  },
  methods: {
    onSubmit() {
      this.$emit('add-todo', this.inputTodo)
      this.inputTodo = ''
    },
    toggle(id) {
      this.$emit('toggle-todo', id)
    }
  }
}
</script>
