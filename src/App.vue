<script setup lang="ts">
import { ref, computed } from "vue";
import { client } from "./trpc";
import ShowInfo from "./components/ShowInfo.vue";
// import { client } from "./trpc";
const txt = ref("");
const helloTxt = computed(() => {
  if (txt.value.length > 0) {
    return "Hello " + txt.value;
  } else {
    return "";
  }
});
const shouldShow = computed(() => txt.value.length > 0);
const alertWelcome = () => {
  alert("Welcome");
};
const addKitten = async (name: string) => {
  const dbKitten = await client.database.addKitten.mutate(name);
  alert(`${dbKitten.name}: ${dbKitten.age}`);
};

const kitten =
  ref<Awaited<ReturnType<(typeof client)["database"]["findKitten"]["query"]>>>(
    null
  );
const findKitten = async (name: string) => {
  const dbKitten = await client.database.findKitten.query(name);
  if (dbKitten) {
    kitten.value = dbKitten;
  } else {
    kitten.value = null;
  }
};
</script>

<template>
  <h1 v-if="shouldShow">Welcome</h1>
  <h1 v-else-if="!shouldShow">Please input your cat's name</h1>
  <h1 @click.meta="() => alertWelcome()">{{ helloTxt }}</h1>
  <input type="text" v-model="txt" />
  <button @click="() => addKitten(txt)">Add Kitten</button>
  <button @click="() => findKitten(txt)">Find Kitten</button>
  <p v-if="kitten">{{ `${kitten.name} is ${kitten.age} years old.` }}</p>
  <p v-else-if="txt.length > 0">Kittens not found</p>
  <ShowInfo :message="txt" />
</template>

<style scoped></style>
