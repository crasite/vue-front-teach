<script setup lang="ts">
import { ref, computed } from "vue";
const txt = ref("");
const helloTxt = computed(() => {
  if (txt.value.length > 0) {
    return "Hello " + txt.value;
  } else {
    return "";
  }
});
const shouldShow = computed(() => txt.value.length > 0);
const alertWelcome = () => {
  alert("Welcome");
};
</script>

<template>
  <h1 v-if="shouldShow">Welcome</h1>
  <h1 v-else-if="!shouldShow">Please input your name</h1>
  <h1 @click="() => alertWelcome()">{{ helloTxt }}</h1>
  <input type="text" v-model="txt" />
</template>

<style scoped></style>
