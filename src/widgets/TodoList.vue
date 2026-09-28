<script setup>
import TodoItem from "./TodoItem.vue";
const { items } = defineProps(["items"]);
</script>

<template>
  <div class="home-page">
    <h3>Todo List</h3>
    <ul>
      <TodoItem
        v-for="item in items"
        :key="item.id"
        v-bind="item"
      />
    </ul>
  </div>
</template>

<style scoped></style>
