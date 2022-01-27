<script>
export default {
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    emitTodo() {
      this.$emit("add-todo", this.todo);
      this.todo = "";
    },
  },
};
</script>

<template>
  <section>
    <label for="todoInput" class="text-xl text-stone-600 dark:text-stone-200"
      >Write a new todo:</label
    >
    <section class="flex gap-4">
      <input
        type="text"
        name="todoInput"
        id="todoInput"
        class="p-1 rounded"
        @keyup.enter="emitTodo()"
        v-model="todo"
      />
      <input
        type="submit"
        class="p-1 rounded cursor-pointer bg-neutral-300"
        value="Add"
        @click="emitTodo()"
      />
    </section>
  </section>
</template>
