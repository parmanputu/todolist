<template>
  <div class="container">
    <form @submit.prevent="onSubmit" class="flex justify-between">
      <input
        type="text"
        class="py-3 px-3 border border-sky-500 w-full text-lg"
        name="inputTodo"
        v-model="inputTodo"
      />
    </form>
  </div>
  <ul class="mt-5">
    <li
      v-for="todo in todos"
      :key="todo.id"
      class="text-lg flex border border-blue-400 p-3 justify-between mb-2"
    >
      <div>
        <input
          type="checkbox"
          name="checkTodo"
          :checked="todo.status === 'done'"
          @change="toggle(todo.id)"
          class="mr-6"
        />
        <span v-if="todo.status === 'done'" class="line-through text-zinc-400">{{
          todo.name
        }}</span>
        <span v-else class="font-bold">{{ todo.name }}</span>
      </div>
      <button @click="remove(todo.id)" class="ml-5">❌</button>
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
  emits: ['add-todo', 'toggle-todo', 'remove-todo'],
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
    },
    remove(id) {
      this.$emit('remove-todo', id)
    }
  }
}
</script>
