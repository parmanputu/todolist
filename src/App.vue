<template>
  <AppHeader title="To-Do List App" />

  <main>
    <AppList :todos @add-todo="addTodo" @toggle-todo="toggleTodo" @remove-todo="removeTodo" />
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
      todos: []
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
    },
    removeTodo(id) {
      const todos = this.todos.filter((todo) => todo.id !== id)
      this.todos = todos
    }
  }
}
</script>
