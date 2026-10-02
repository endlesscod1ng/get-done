<script setup>
import { ref, defineEmits, onMounted, watch } from "vue";

const { item } = defineProps(["item"]);
const currentItem = ref({});

const emit = defineEmits(["updateItem", "cancelEdit"]);
const onSubmit = () => {
  emit("updateItem", currentItem.value);
};
const onCancel = () => emit("cancelEdit");
watch(
  () => item,
  (newValue) => {
    currentItem.value = newValue;
  },
);
onMounted(() => {
  currentItem.value = { ...item };
});
</script>
<template>
  <div class="edit-form">
    <h3>Edit item</h3>
    <form @submit.prevent="onSubmit">
      <input
        v-model="currentItem.text"
        type="text"
      />
      <button type="submit">Update</button>
      <button
        type="button"
        @click="onCancel"
      >
        Cancel
      </button>
    </form>
  </div>
</template>

<style scoped></style>
