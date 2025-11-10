<template>
  <div class="task-card">
    <header>
      <div><b>{{ task.title }}</b></div>
    </header>

    <main>
      <div>{{ task.text }}</div>
      <slot></slot>
    </main>

    <footer>
      <button type="button" @click="completeTask">Выполнено</button>
    </footer>
  </div>
</template>

<script setup lang="ts">
const props = defineProps<{
  task: { id: number; title: string; text: string };
}>();

function completeTask() {
  alert(`Задача "${props.task.title}" выполнена!`);
}
</script>

<style scoped>
.task-card {
  display: flex;
  gap: 4px;
  flex-direction: column;
  border: 1px solid #ccc;
  padding: 12px;
  border-radius: 8px;
  margin-bottom: 8px;
}

.task-card header {
  font-size: 1.1em;
}

.task-card main {
  color: #666;
}

.task-card footer button {
  background-color: #000000;
  color: rgb(0, 0, 0);
  border: none;
  padding: 6px 12px;
  border-radius: 4px;
  cursor: pointer;
}

.task-card footer button:hover {
  background-color: #45a049;
}
</style>