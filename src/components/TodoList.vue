<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeTodo(index) {
      this.$emit("remove-todo", index);
    },
    toggleFinished(index) {
      this.$emit("finished-todo", index);
    },
  },
};
</script>

<template>
  <ul v-if="todos.length !== 0" class="flex flex-col gap-2 p-2 rounded bg-slate-200">
    <li
      v-for="todo in todos"
      :key="todo"
      class="flex gap-2 p-1 rounded shadow-md bg-neutral-300"
    >
      <p
        class="p-1 rounded-lg"
        :style="{ textDecoration: todo.finished ? 'line-through' : 'none' }"
      >
        {{ todo.name }}
      </p>
      <nav class="flex gap-2 ml-auto">
        <button
          class="p-1 transition-colors bg-green-300 rounded-lg hover:bg-green-400"
          @click="toggleFinished(todos.indexOf(todo))"
        >
          Done
        </button>
        <button
          class="text-sm [text-shadow:_2px_2px_2px_#000] text-red-600"
          @click="removeTodo(todos.indexOf(todo))"
        >
          x
        </button>
      </nav>
    </li>
  </ul>
</template>
