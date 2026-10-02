<script setup>
import { computed, ref } from "vue";
import TodoList from "../widgets/TodoList.vue";
import AddForm from "../widgets/AddForm.vue";
import EditForm from "../widgets/EditForm.vue";
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
const item = ref(null);

const addItem = (text) => {
  items.value.push({ id: items.value.length + 1, text });
};
const removeItem = (id) => {
  items.value = items.value.filter((item) => item.id !== id);
};
const updateItem = (updatedItem) => {
  items.value = items.value.map((item) =>
    item.id === updatedItem.id ? { ...updatedItem } : item,
  );
  item.value = null;
};
const editItem = (id) => {
  item.value = items.value.find((item) => item.id === id);
};

const cancelEdit = () => (item.value = null);

const action = computed(() => (item.value ? "edit" : "add"));
// 52.45
</script>

<template>
  <div class="home-page">
    <TodoList
      :items="items"
      @removeItem="removeItem"
      @editItem="editItem"
    />
    <AddForm
      v-if="action === 'add'"
      @addItem="addItem"
    />
    <EditForm
      v-if="action === 'edit'"
      :item="item"
      @updateItem="updateItem"
      @cancelEdit="cancelEdit"
    />
  </div>
</template>

<style scoped></style>
