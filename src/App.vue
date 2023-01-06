<script setup></script>

<template>
  <!--Все изучается на практике -->

  <!-- hover модификатор наведения -->
  <h1 class="text-4xl hover:text-lime-400 cursor-pointer">Hello</h1>

  <!--space добавляет отступы внутри между каждым элементом-->
  <div class="w-min mx-auto space-y-6">
    <div>
      <p class="text-left ml-2">Логин</p>

      <!--rounded округление-->
      <!--focus модификатор фокусироки на элементе-->
      <!--В этом поле ввода обводка убирается при расфокусировке (при выборе заметно как внутри элемента происходит смещение)-->
      <input
        type="text"
        placeholder="Текст"
        class="bg-zinc-700 rounded-lg focus:border-2 border-red-400 outline-none px-4 py-2 h-8 w-72 font-bold"
      />
    </div>
    <div>
      <p class="text-left ml-2">Пароль</p>
      <!--В этом поле ввода обводка становится прозрачной при расфокусировке (элемент нечего не смещает внутри)-->
      <input
        type="text"
        placeholder="Текст"
        class="bg-zinc-700 rounded-lg border-transparent border-2 focus:border-red-400 outline-none px-4 py-2 h-8 w-72 font-bold"
      />
    </div>
  </div>

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
