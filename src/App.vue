<template>
  <!--Все изучается на практике -->

  <!-- hover модификатор наведения -->
  <FormLogin v-model:email="bufEmail" v-model:password="bufPassword" @create="OnCreate" />

  <hr class="my-5 border-gray-600" />

  <div class="space-y-4">
    <FormItem
      v-for="(item, i) in listItems"
      :login="item.email"
      :password="item.password"
      @close="OnRemove(i)"
      @click="updateItem = item"
    />
  </div>

  <FormEdit
    v-if="updateItem"
    :login="updateItem.email"
    :password="updateItem.password"
    @save="OnSave"
    @close="updateItem = undefined"
  >
  </FormEdit>
</template>

<script setup>
import { ref, watch } from "vue";

import FormLogin from "./components/FormLogin.vue";
import FormItem from "./components/FormItem.vue";
import FormEdit from "./components/FormEdit.vue";

const bufEmail = ref("");
const bufPassword = ref("");

const listItems = ref([
  {
    email: "LOGIN",
    password: "PASS",
  },
  {
    email: "ewfewv",
    password: "ecfwedef",
  },
]);
const updateItem = ref();

watch(updateItem, (item) => {
  if (item) console.log(item.email);
});

const OnCreate = (email, password) => {
  listItems.value.push({
    email,
    password,
  });
};

const OnRemove = (idx) => {
  listItems.value.splice(idx, 1);
};

const OnSave = (email, password) => {
  if (!updateItem.value) return;

  updateItem.value.email = email;
  updateItem.value.password = password;
  updateItem.value = undefined;
};
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
