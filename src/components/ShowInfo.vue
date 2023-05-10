<script setup lang="ts">
defineProps({
  message: String,
});
defineEmits<{
  (e: "clearText"): void;
}>();
</script>

<template>
  <h1>Hello {{ message }}</h1>
  <button
    @click="
      () => {
        $emit('clearText');
      }
    "
  >
    Clear Text
  </button>
</template>
