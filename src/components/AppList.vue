<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input
        type="text"
        class="py-3 px-3 border border-sky-500 text-sm mr-2"
        name="inputTodo"
        v-model="inputTodo"
      />
      <button type="submit" class="rounded-md bg-slate-600 text-white py-3 px-3">Add Todo</button>
    </form>
  </div>
  <ul class="mt-5">
    <li v-for="todo in todos" :key="todo.id" class="text-lg">
      <input
        type="checkbox"
        name="checkTodo"
        :checked="todo.status === 'done'"
        @change="toggle(todo.id)"
        class="mr-3"
      />
      <span v-if="todo.status === 'done'" class="line-through text-zinc-400">{{ todo.name }}</span>
      <span v-else class="font-bold">{{ todo.name }}</span>
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
