<template>
  <!--Все изучается на практике -->

  <!-- hover модификатор наведения -->
  <FormLogin @create="OnCreate"> </FormLogin>

  <hr class="my-5 border-gray-600" />

  <div class="space-y-4">
    <FormItem
      v-for="(item, i) in listItems"
      :login="item.email"
      :password="item.password"
      @close="OnRemove(i)"
      @click="isEdit = true"
    />
  </div>

  <FormEdit v-if="isEdit" @close="isEdit = false"> </FormEdit>
</template>

<script setup>
import { ref } from "vue";

import FormLogin from "./components/FormLogin.vue";
import FormItem from "./components/FormItem.vue";
import FormEdit from "./components/FormEdit.vue";

const listItems = ref([
  {
    email: "LOGIN",
    password: "PASS",
  },
]);

const OnCreate = (email, password) => {
  listItems.value.push({
    email,
    password,
  });
};

const OnRemove = (idx) => {
  listItems.value.splice(idx, 1);
};

const isEdit = ref(false);
</script>

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
