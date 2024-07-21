<template>
  <AppHeader title="To-Do List App" />

  <main>
    <AppList :todos @add-todo="addTodo" @toggle-todo="toggleTodo" />
  </main>
</template>

<script>
import AppHeader from './components/AppHeader.vue'
import AppList from './components/AppList.vue'

export default {
  name: 'App',
  components: {
    AppHeader,
    AppList
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          name: 'Learn vue.js',
          status: 'inprogress'
        },
        {
          id: 2,
          name: 'Tailwind',
          status: 'done'
        }
      ]
    }
  },
  methods: {
    addTodo(todo) {
      const data = {
        id: this.todos.length + 1,
        name: todo,
        status: 'inprogress'
      }
      this.todos.push(data)
    },
    toggleTodo(id) {
      const todo = this.todos.find((todo) => todo.id === id)
      if (todo) {
        todo.status = todo.status === 'done' ? 'inprogress' : 'done'
      }
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
