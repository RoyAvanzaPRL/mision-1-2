<template>
    <h3>Lista de tareas: {{ tasks.length }}</h3>
    <ul class="task-list">
      <!-- :key="task.id" this task has a unique id
       :task="task" this sends this task to the TaskItem component
       $event has the id of the task -->
      <TaskItem
      v-for="task in tasks"
      :key="task.id" 
      :task="task"
      @toggle-task="emit('toggle-task', $event)"
      @delete-task="emit('delete-task', $event)"
    />
    </ul>
</template>

<script setup lang="ts">
import type { Task } from '../types.ts';
import TaskItem from './TaskItem.vue';

// Defines the things that the component gets from the parent
const props = defineProps<{
  tasks: Task[];
}>();

// The events that the component sends
const emit = defineEmits<{
  'toggle-task': [id: number],
  'delete-task': [id: number]
}>();
</script>