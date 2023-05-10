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
  todos.value = todos.value.filter((v) => v.id != id);
};

const editTodoHandler = (id: number, text: string) => {
  todos.value = todos.value.map((todo) => {
    if (todo.id == id) {
      return { text, id };
    } else {
      return todo;
    }
  });
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
