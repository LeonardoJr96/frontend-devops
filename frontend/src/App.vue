<template>
  <div>
    <h1>Tasks</h1>
    <ul>
      <li v-for="task in tasks" :key="task.id">
        {{ task.title }} - <strong>{{ task.done ? 'Done' : 'Pending' }}</strong>
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const tasks = ref([])

onMounted(async () => {
  const response = await axios.get('http://localhost:8000/api/tasks/')
  tasks.value = response.data
})
</script>
