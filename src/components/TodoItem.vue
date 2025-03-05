<script setup>
defineProps(["todo"]);
const emit = defineEmits(["delete", "toggle"]);
</script>

<template>
  <li :class="{ completed: todo.completed }">
    <input type="checkbox" :checked="todo.completed" @change="emit('toggle', todo.id)" />
    {{ todo.text }}
    <button @click="emit('delete', todo.id)">❌</button>
  </li>
</template>

<style scoped>
li {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 8px;
  border-bottom: 1px solid #ccc;
}
.completed {
  text-decoration: line-through;
  color: gray;
}
</style>
