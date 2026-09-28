<script setup>
import { ref, defineEmits } from "vue";

const text = ref("");
const emit = defineEmits(["addItem"]);
const onSubmit = () => {
  emit("addItem", text.value);
  text.value = "";
};
</script>
<template>
  <div class="add-form">
    <h3>Add item</h3>
    {{ text }}
    <form
      @submit.prevent="onSubmit"
      action=""
    >
      <input
        v-model="text"
        type="text"
      />
      <button type="submit">Add</button>
    </form>
  </div>
</template>

<style scoped></style>
