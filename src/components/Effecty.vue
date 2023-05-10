<script setup lang="ts">
import { ref } from "vue";
defineProps<{ modelValue?: string }>();
defineEmits<{
  (e: "update-value", v: string, i: number): void;
  (e: "update:modelValue", v: string): void;
}>();

const msg = ref("");
</script>

<template>
  <input
    type="text"
    v-model="msg"
    @input="
      () => {
        $emit('update-value', msg, msg.length);
        $emit('update:modelValue', msg);
      }
    "
  />
</template>

<style scoped></style>
