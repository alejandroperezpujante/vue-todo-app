<script>
import TodoList from "./components/TodoList.vue";
import TodoInput from "./components/TodoInput.vue";
export default {
  components: {
    TodoList,
    TodoInput,
  },
  data() {
    return {
      todos: [{ finished: false, name: "Add a new todo" }],
    };
  },
  methods: {
    addTodo(todo) {
      if (todo !== "") {
        console.log(todo);
        this.todos.push({ finished: false, name: todo });
        this.todo = "";
      } else {
        console.log(todo);
        alert("Todo must have a value");
      }
    },
    removeTodo(index) {
      this.todos.splice(index, 1);
    },
    toggleFinishedTodo(index) {
      this.todos[index].finished = !this.todos[index].finished;
    },
  },
};
</script>

<template>
  <header>
    <h1 class="font-mono text-center dark:text-stone-200 text-2xl">Vue 3 Todo App</h1>
  </header>
  <main class="grid gap-y-3 place-content-center">
    <TodoInput @add-todo="addTodo" />
    <TodoList
      :todos="todos"
      @remove-todo="removeTodo"
      @finished-todo="toggleFinishedTodo"
    />
  </main>
</template>
