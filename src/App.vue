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
</script>

<template>
  <h1>{{ helloTxt }}</h1>
  <input type="text" v-model="txt" />
</template>

<style scoped></style>
