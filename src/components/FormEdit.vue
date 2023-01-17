<template>
  <div
    class="flex fixed top-0 left-0 h-screen w-screen bg-[#0000008f] justify-center items-center"
  >
    <div class="relative bg-gray-600 p-6 min-w-[450px] min-h-[200px] rounded-lg">
      <FormLogin @create="OnUpdate">
        <template #header> <h6 class="font-bold text-xl">Обновить</h6> </template>
        <template #submit>
          <button
            type="submit"
            class="bg-blue-500 px-6 py-2 rounded-lg hover:bg-blue-700 transition-colors"
          >
            Обновить
          </button>
        </template>
      </FormLogin>
      <button
        class="absolute top-2 right-4 hover:text-red-700 font-bold"
        @click="OnClose"
      >
        X
      </button>
    </div>
  </div>
</template>

<script setup>
import FormLogin from "./FormLogin.vue";

defineProps({
  login: { type: String, required: true },
  password: { type: String, required: true },
});

const emit = defineEmits(["close", "save"]);

const OnUpdate = () => {
  emit("save");
};
const OnClose = () => {
  emit("close");
};
</script>
