<script setup>
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import WelcomeCard from "./components/WelcomeCard.vue";
import Todos from "./components/Todos.vue";
</script>

<template>
  <header>
    <WelcomeCard />
  </header>
  <main class="grid gap-y-3 place-content-center">
    <Todos />
  </main>
</template>
