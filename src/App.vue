<script setup lang="ts">
// import HelloWorld from './components/HelloWorld.vue'
import TodoList from './components/TodoList.vue';
</script>

<template>
  <!-- <HelloWorld msg="All Is One" /> -->
  <div class="container">
    <h1>Vue To-Do List ✅</h1>
    <TodoList />
  </div>
</template>

<style scoped>
.container {
  max-width: 400px;
  margin: auto;
  text-align: center;
}
</style>
