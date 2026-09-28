<script setup>
const { id,text } = defineProps(["id","text"]);
</script>
<template>
  <li
    class="todo-item"
    :data-id="id"
  >
    {{ text }}
  </li>
</template>

<style scoped></style>
