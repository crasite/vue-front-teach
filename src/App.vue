<script setup lang="ts">
import { ref } from "vue";
import ShowInfo from "./components/ShowInfo.vue";

const txt = ref("");
const clearTextHandler = () => {
  txt.value = "";
};
</script>

<template>
  <ShowInfo :message="txt" @clear-text="clearTextHandler" />
  <input type="text" v-model="txt" />
</template>

<style scoped></style>
