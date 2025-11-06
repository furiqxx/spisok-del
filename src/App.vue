<template>
  <div>
    <h1>СПИСОК ДЕЛ</h1>

    <p>Всего задач: {{ tasksCount }}</p>

    <div class="tasks">
      <div 
        v-for="task in tasks" 
        :key="task.id"  
        class="task-card"
      >
        <header>
          <h3>{{ task.title }}</h3>
        </header>

        <main>
          <p>{{ task.text }}</p>
          <span v-if="task.isUrgent" class="urgent">СРОЧНО! 🔥</span>
        </main>

        <footer>
          <button type="button" @click="completeTask(task)">Выполнено</button>
        </footer>
      </div>
    </div>

    <p v-if="tasks.length === 0">Задачи отсутствуют</p>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from "vue";

const tasks = ref([
  { id: 1, title: "Посетить колледж", text: "Желательно все пары", isUrgent: true },
  { id: 2, title: "Сделать домашнее задание", text: "Желательно полностью" },
  { id: 3, title: "Встретиться с друзьями", text: "", isUrgent: true },
  { id: 4, title: "Выспаться", text: "Что то невозможное" },
]);

const tasksCount = computed(() => {
  return `${tasks.value.length} задач`;
});

function completeTask(task: any) {
  alert(`Задача "${task.title}" выполнена!`);
}
</script>

<style>
.tasks {
  display: flex;
  gap: 16px;
  flex-direction: column;
  max-width: 500px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  text-align: center;
  color: #333;
  margin-bottom: 20px;
}

.task-card {
  display: flex;
  flex-direction: column;
  border: 1px solid #ccc;
  padding: 16px;
  border-radius: 8px;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.task-card header h3 {
  margin: 0 0 8px 0;
  color: #2c3e50;
}

.task-card main p {
  margin: 0 0 8px 0;
  color: #666;
}

.task-card .urgent {
  color: #ff4444;
  font-weight: bold;
  font-size: 14px;
}

.task-card footer button {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  cursor: pointer;
  font-weight: bold;
}

.task-card footer button:hover {
  background-color: #45a049;
}
</style>