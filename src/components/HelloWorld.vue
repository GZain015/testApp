<script setup lang="ts">
import { ref } from 'vue'

defineProps<{ msg: string }>()

const count = ref(0)
</script>

<template>
  <h1>{{ msg }}</h1>
  <div class="card">
    <button type="button" @click="count++" class="btn">count is {{ count }}</button>
    <br>
    <input type="color" class="m-1" @click="count++"/>
  </div>

</template>

<style scoped>
.read-the-docs {
  color: #888;
}
.m-1 {
  margin: 1em;
  padding: 2em;
  border-radius: 15em;
}
.btn {
  background-color: #42b883;
}
</style>
