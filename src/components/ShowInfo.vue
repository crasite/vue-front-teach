<script setup lang="ts">
defineProps({
  message: String,
});
</script>

<template>
  <h1>Hello {{ message }}</h1>
</template>
