<script setup>
import FormLogin from "./components/FormLogin.vue";
</script>

<template>
  <!--Все изучается на практике -->

  <!-- hover модификатор наведения -->
  <FormLogin>PC</FormLogin>

  <div class="flex flex-col lg:flex-row mx-auto my-24 space-x-10">
    <a href="https://vitejs.dev" target="_blank">
      <img src="/vite.svg" class="h-72" alt="Vite logo" />
    </a>
    <a href="https://vuejs.org/" target="_blank">
      <img src="./assets/vue.svg" class="h-72" alt="Vue logo" />
    </a>
  </div>
</template>

<style>
@tailwind base;
@tailwind components;
@tailwind utilities;

html,
body {
  @apply bg-[#242424] text-white;
}

#app {
  @apply my-6 mx-auto text-center w-min h-min;
}
</style>
