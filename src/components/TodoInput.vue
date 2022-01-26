<script>
export default {
  data() {
    return {
      todo: "",
    };
  },
  methods: {
    sendTodo() {
      this.$emit("add-todo", this.todo);
      this.todo = "";
    },
  },
};
</script>

<template>
  <form @submit.prevent="refresh" class="flex flex-col gap-2">
    <label for="todoInput" class="text-stone-200 text-xl">Write a new todo:</label>
    <section class="flex gap-4">
      <input
        type="text"
        name="todoInput"
        id="todoInput"
        class="rounded p-1"
        v-model="todo"
      />
      <input
        type="submit"
        class="p-1 rounded bg-neutral-300 cursor-pointer"
        value="Add"
        @click="sendTodo()"
      />
    </section>
  </form>
</template>
