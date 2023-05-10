<script setup lang="ts">
import { ref } from "vue";
import ShowInfo from "./components/ShowInfo.vue";

const txt = ref("");
const clearTextHandler = () => {
  txt.value = "";
};
const countHandler = (n: number) => {
  alert(n);
};
</script>

<template>
  <ShowInfo
    :message="txt"
    @clear-text="clearTextHandler"
    @increase-count="countHandler"
  />
  <input type="text" v-model="txt" />
</template>

<style scoped></style>
