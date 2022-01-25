<script setup>
import { ref } from "vue";
const todos = ref([{ finished: false, name: "Add a new todo" }]);
const todo = ref("");

function addTodo(todo) {
  if (todo !== "") {
    todos.value.push({ finished: false, name: todo });
  } else {
    alert("Todo must have a value");
  }
}

function removeTodo(todo) {
  todos.value.splice(todos.value.indexOf(todo), 1);
}

function toggleFinished(todo) {
  todo.finished = !todo.finished;
}
</script>

<template>
  <h3 class="text-lg dark:text-stone-200">Write a new todo:</h3>
  <section class="flex gap-2">
    <input
      type="text"
      name="todoInput"
      id="todoInput"
      @keypress.enter="addTodo(todo)"
      class="p-1 rounded"
      v-model="todo"
    />
    <button class="p-1 rounded bg-neutral-300" @click="addTodo(todo)">Add</button>
  </section>

  <ul v-if="todos.length !== 0" class="flex flex-col gap-2 p-2 rounded bg-slate-200">
    <li
      v-for="todo in todos"
      :key="todo"
      class="flex gap-2 p-1 rounded shadow-md bg-neutral-300"
    >
      <p
        class="rounded-lg p-1"
        :style="{
          textDecoration: todo.finished ? 'line-through' : 'none',
          backgroundColor: todo.finished ? '#3d3d3d' : 'transparent',
        }"
      >
        {{ todo.name }}
      </p>
      <nav class="flex gap-2 ml-auto">
        <button
          class="p-1 transition-colors bg-green-300 rounded-lg hover:bg-green-400"
          @click="toggleFinished(todo)"
        >
          Done
        </button>
        <button
          class="text-sm [text-shadow:_2px_2px_2px_#000] text-red-600"
          @click="removeTodo(todo)"
        >
          x
        </button>
      </nav>
    </li>
  </ul>
</template>
