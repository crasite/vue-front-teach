<script setup lang="ts">
import { ref } from "vue";
const count = ref(0);
defineProps({
  message: String,
});

defineEmits<{
  (e: "clearText"): void;
  (e: "increaseCount", v: number): void;
}>();
</script>

<template>
  <h1>Hello {{ message }}</h1>
  <button
    @click="
      () => {
        count += 1;
        $emit('clearText');
        $emit('increaseCount', count);
      }
    "
  >
    Clear Text
  </button>
</template>
