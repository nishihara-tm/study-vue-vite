<template>
  <DataTable :value="tasks" responsiveLayout="scroll">
    <Column field="id" header="Id"></Column>
    <Column field="title" header="Title"></Column>
    <Column field="content" header="Content"></Column>
    <Column filed="modify" header="変更">
      <template #body="slotProps">
          <Button icon="pi pi-pencil" class="p-button-rounded p-button-success mr-2" @click="modifyTask(slotProps.data.id)" />
          <Button icon="pi pi-trash" class="p-button-rounded p-button-warning" @click="deleteTask(slotProps.data.id)" />
      </template>
    </Column>
  </DataTable>
</template>

<script setup lang="ts">
import { Task } from "../models/Task"
import { computed, ref } from 'vue'

const props = defineProps<{ tasks: Task[] }>()
const emit = defineEmits(['update:task', 'delete:task'])

const modifyTask = (id: number) => {
  emit('update:task', id)
}

const deleteTask = (id: number) => {
  emit('delete:task', id)
}

</script>

<style scoped>
.block {
  margin-bottom: 30px;
}

span {
  margin-right: 20px;
}
</style>
