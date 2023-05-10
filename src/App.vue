<script setup lang="ts">
import Effecty from "./components/Effecty.vue";
import { ref } from "vue";
import { z } from "zod";
const msg = ref("");
const car = ref("");
const updateHandler = (v: string, i: number) => {
  const text = z.string().min(1).max(10).safeParse(v);
  if (!text.success) {
    msg.value = "Wrong input";
  } else {
    msg.value = `${text.data} (${i})`;
  }
};
</script>

<template>
  <Effecty @update-value="updateHandler" v-model="car" />
  <h1>{{ msg }}</h1>
  <h2>{{ car }}</h2>
</template>

<style scoped></style>
