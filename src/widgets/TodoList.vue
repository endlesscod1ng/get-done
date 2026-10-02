<script setup>
import { defineEmits } from "vue";
import TodoItem from "./TodoItem.vue";

const { items } = defineProps(["items"]);
const emit = defineEmits(["removeItem", "editItem"]);

const removeItem = (id) => {
  emit("removeItem", id);
};
const editItem = (id) => {
  emit("editItem", id);
};
</script>

<template>
  <div class="home-page">
    <h3>Todo List</h3>
    <ul>
      <TodoItem
        v-for="item in items"
        :key="item.id"
        v-bind="item"
        @removeItem="removeItem(item.id)"
        @editItem="editItem(item.id)"
      />
    </ul>
  </div>
</template>

<style scoped></style>
