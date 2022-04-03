<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup
import TaskList from './components/TaskList.vue'
import { Task } from "../models/Task"
import { computed, reactive, ref } from 'vue'

const tasks = reactive<Task[]>([
  {
    id: 1,
    title: "hello",
    content: "world"
  },
  {
    id: 2,
    title: "hello2",
    content: "worlds"
  }
])

const handleUpdate = (id: number) => {
  const task = tasks.find(t => t.id === id)
  if (task) {
    task.title += "1"
  }
}

const handleDelete = (id: Number) => {
  const i = tasks.findIndex(t => t.id === id)
  if (i >= 0) {
    tasks.splice(i, 1)
  }
}
</script>

<template>
  <TaskList
    :tasks="tasks"
    @update:task="handleUpdate"
    @delete:task="handleDelete"
  />
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
