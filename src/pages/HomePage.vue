<script setup>
import { ref } from "vue";
import TodoList from "../widgets/TodoList.vue";
import AddForm from "../widgets/AddForm.vue";
const items = ref([
  {
    id: 1,
    text: "Learn Vue",
  },
  {
    id: 2,
    text: "Learn React",
  },
  {
    id: 3,
    text: "Learn React Native",
  },
]);

const addItem = (text) => {
  items.value.push({ id: items.value.length + 1, text });
};
// 29.55
</script>

<template>
  <div class="home-page">
    <AddForm @addItem="addItem" />
    <TodoList :items="items" />
  </div>
</template>

<style scoped></style>
