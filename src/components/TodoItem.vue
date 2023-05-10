<script setup lang="ts">
import { ref } from "vue";
const props = defineProps<{
  message: string;
  id: number;
}>();
const emit = defineEmits<{
  (e: "removeItem", id: number): void;
  (e: "editItem", id: number, text: string): void;
}>();
const isDone = ref(false);
const editHandler = () => {
  const newMessage = prompt("New Message");
  if (newMessage) {
    emit("editItem", props.id, newMessage);
  }
};
</script>

<template>
  <div>
    <span :class="isDone ? `done` : ``" @click="() => (isDone = !isDone)">{{
      message
    }}</span>
    <button @click="$emit('removeItem', id)">Remove</button>
    <button @click="editHandler">Edit</button>
  </div>
</template>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>
