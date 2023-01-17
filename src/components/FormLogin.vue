<template>
  <form @submit.prevent="OnSubmit">
    <slot name="header"><h5>Login</h5></slot>
    <!--space добавляет отступы внутри между каждым элементом-->
    <div class="w-min mx-auto space-y-6">
      <div>
        <p class="text-left ml-2">Логин</p>

        <!--rounded округление-->
        <!--focus модификатор фокусироки на элементе-->
        <!--В этом поле ввода обводка убирается при расфокусировке (при выборе заметно как внутри элемента происходит смещение)-->
        <input
          v-model="email"
          type="text"
          placeholder="Текст"
          class="bg-zinc-700 rounded-lg focus:border-2 border-red-400 outline-none px-4 py-2 h-8 w-72 font-bold"
        />
      </div>
      <div>
        <p class="text-left ml-2">Пароль</p>
        <!--В этом поле ввода обводка становится прозрачной при расфокусировке (элемент нечего не смещает внутри)-->
        <input
          v-model="password"
          type="text"
          placeholder="Текст"
          class="bg-zinc-700 rounded-lg border-transparent border-2 focus:border-red-400 outline-none px-4 py-2 h-8 w-72 font-bold"
        />
      </div>
      <slot name="submit"
        ><button
          type="submit"
          class="bg-green-600 px-6 py-2 rounded-lg hover:bg-green-800 transition-colors"
        >
          Вход
        </button></slot
      >
    </div>
  </form>
</template>

<script setup>
import { ref } from "vue";

defineProps({});

const emit = defineEmits(["create"]);

const email = ref("");
const password = ref("");

/**
 *
 * @param {HTMLFormElement} e
 */
const OnSubmit = (e) => {
  if (!email.value.length || !password.value.length) return;

  emit("create", email.value, password.value);
};
</script>
