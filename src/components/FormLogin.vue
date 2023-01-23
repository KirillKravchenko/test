<template>
  <form @submit.prevent="OnSubmit">
    <slot name="header" :email="Email"><h5>Login</h5></slot>
    <!--space добавляет отступы внутри между каждым элементом-->
    <div class="w-min mx-auto space-y-6">
      <div>
        <p class="text-left ml-2">Логин</p>

        <!--rounded округление-->
        <!--focus модификатор фокусироки на элементе-->
        <!--В этом поле ввода обводка убирается при расфокусировке (при выборе заметно как внутри элемента происходит смещение)-->
        <input
          v-model="Email"
          type="text"
          placeholder="Текст"
          class="bg-zinc-700 rounded-lg focus:border-2 border-red-400 outline-none px-4 py-2 h-8 w-72 font-bold"
        />
      </div>
      <div>
        <p class="text-left ml-2">Пароль</p>
        <!--В этом поле ввода обводка становится прозрачной при расфокусировке (элемент нечего не смещает внутри)-->
        <input
          v-model="Password"
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
import { computed } from "vue";

const props = defineProps({
  email: String,
  password: String,
});

const emit = defineEmits(["create", "update:email", "update:password"]);

const Email = computed({
  get: () => props.email,
  set: (value) => {
    emit("update:email", value);
  },
});
const Password = computed({
  get: () => props.password,
  set: (value) => {
    emit("update:password", value);
  },
});

/**
 *
 * @param {HTMLFormElement} e
 */
const OnSubmit = (e) => {
  if (!Email.value.length || !Password.value.length) return;

  emit("create", Email.value, Password.value);
};
</script>
