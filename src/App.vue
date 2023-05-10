<script setup lang="ts">
import { ref } from "vue";
import ShowInfo from "./components/ShowInfo.vue";

const txt = ref("");
const items = ref([{ message: "Foo" }, { message: "Bar" }, { message: "Baz" }]);
</script>

<template>
  <ShowInfo :message="txt" />
  <input type="text" v-model="txt" />
  <ShowInfo v-for="item in items" :message="item.message" :key="item.message" />
</template>

<style scoped></style>
