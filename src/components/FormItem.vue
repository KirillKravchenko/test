<template>
  <div class="relative bg-neutral-700 py-9 rounded-lg">
    <h6>Логин: {{ login }}</h6>
    <h6>Пароль: {{ password }}</h6>
    <button class="absolute top-2 right-4 hover:text-red-700 font-bold" @click="OnClose">
      X
    </button>
  </div>
</template>

<script setup>
defineProps({
  login: { type: String, required: true },
  password: { type: String, required: true },
});

const emit = defineEmits(["close"]);

const OnClose = () => {
  emit("close");
};
</script>
