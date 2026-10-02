<script setup>
import { defineEmits } from "vue";

const emit = defineEmits(["removeItem", "editItem"]);

const { id, text } = defineProps(["id", "text"]);
const removeItem = () => {
  emit("removeItem", id);
};
const editItem = () => {
  emit("editItem", id);
};
</script>
<template>
  <li
    class="todo-item"
    :data-id="id"
  >
    <p>
      {{ text }}
    </p>
    <button @click="removeItem(id)">Remove</button>
    <button @click="editItem(id)">Edit</button>
  </li>
</template>

<style scoped></style>
