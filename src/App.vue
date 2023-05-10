<script setup lang="ts">
import { ref } from "vue";
import TodoItem from "./components/TodoItem.vue";
type Todo = {
  text: string;
  id: number;
};
const txt = ref("");
const currentId = ref(0);
const todos = ref<Todo[]>([]);
const addNewTodo = () => {
  if (txt.value != "") {
    todos.value.push({
      text: txt.value,
      id: currentId.value,
    });
    txt.value = "";
    currentId.value += 1;
  }
};

const removeTodoHandler = (id: number) => {
  const idx = todos.value.findIndex((v) => v.id == id);
  if (idx >= 0) {
    todos.value.splice(idx, 1);
  }
};

const editTodoHandler = (id: number, text: string) => {
  const todo = todos.value.find((v) => v.id == id);
  if (todo) {
    todo.text = text;
  }
};
</script>

<template>
  <div>
    <p>Add New Todo</p>
    <input type="text" v-model="txt" />
    <button @click="addNewTodo">Add</button>
    <TodoItem
      @remove-item="removeTodoHandler"
      @edit-item="editTodoHandler"
      v-for="todo in todos"
      :message="todo.text"
      :id="todo.id"
      :key="todo.id"
    />
  </div>
</template>

<style scoped></style>
