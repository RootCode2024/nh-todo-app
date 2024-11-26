<script setup>
import { ref } from 'vue'

const tasks = ref([])

const newTask = ref('')


const addTask = (event) => {
  event.preventDefault()
  if (newTask.value.trim()) {
    tasks.value.push(newTask.value.trim())
    newTask.value = ''
  }
}
</script>

<template>
  <main class="app-container">
    <h1>NH TODO APP</h1>

    <!-- Ajouter une tâche -->
    <section class="add-task">
      <h2>Ajouter une tâche</h2>
      <form @submit="addTask">
        <input 
          v-model="newTask" 
          type="text" 
          placeholder="Ajouter une tâche" 
          class="task-input"
        />
        <button type="submit" class="add-button" :class="{ 'add-button-disabled': !newTask }">Ajouter</button>
      </form>
    </section>

    <!-- Liste des tâches -->
    <section class="task-list" v-if="tasks.length">
      <h2>Liste des tâches</h2>
      <ul>
        <li v-for="(task, index) in tasks" :key="index" class="task-item">
          {{ task }}
        </li>
      </ul>
    </section>
    <p v-else>Aucune tâche pour le moment.</p>
  </main>
</template>

<style scoped>
.app-container {
  @apply max-w-screen-md mx-auto p-4;
  font-family: Arial, sans-serif;
  text-align: center;
}

h1 {
  @apply text-3xl font-bold;
}

.add-task, .task-list {
  @apply mt-8;
}

.task-input {
  @apply w-3/4 p-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-400;
}

.add-button {
  @apply ml-2 px-4 py-2 bg-blue-500 text-white rounded-lg hover:bg-blue-600;
}

.task-item {
  @apply p-2 mt-2 bg-gray-100 border border-gray-300 rounded-lg;
}

.add-button-disabled {
  @apply opacity-50 cursor-not-allowed;
}
</style>
