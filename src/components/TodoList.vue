<script setup>
import { ref, watch } from "vue";
import TodoItem from "./TodoItem.vue";

// Reactive to-do list
const todos = ref(JSON.parse(localStorage.getItem("todos")) || []);
const newTask = ref("");

// Add a new task
const addTodo = () => {
  if (newTask.value.trim()) {
    todos.value.push({ id: Date.now(), text: newTask.value, completed: false });
    newTask.value = "";
  }
};

// Delete a task
const deleteTodo = (id) => {
  todos.value = todos.value.filter(todo => todo.id !== id);
};

// Toggle task completion
const toggleComplete = (id) => {
  const todo = todos.value.find(todo => todo.id === id);
  if (todo) todo.completed = !todo.completed;
};

// Watch and save to localStorage
watch(todos, () => {
  localStorage.setItem("todos", JSON.stringify(todos.value));
}, { deep: true });
</script>

<template>
  <div>
    <input v-model="newTask" @keyup.enter="addTodo" placeholder="Add a task..." />
    <button @click="addTodo">➕</button>

    <ul>
      <TodoItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @delete="deleteTodo"
        @toggle="toggleComplete"
      />
    </ul>
  </div>
</template>

<style scoped>
input {
  padding: 8px;
  width: 70%;
}
button {
  padding: 8px;
  cursor: pointer;
}
ul {
  list-style: none;
  padding: 0;
}
</style>
