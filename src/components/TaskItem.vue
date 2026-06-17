<template>
  <!-- Vue lets you create things like this :class="{ done: task.done }"
   this says that if the item has done = true, it has this class; if not, it has the other class -->
  <li
    class="task-item"
    :class="{ done: task.done }"
    @click="emit('toggle-task', task.id)"
  >
    <span class="task-title">{{ task.title }}</span>
    <!-- Stops the event before it reaches the toggle-task event -->
    <button
      type="button"
      class="delete-btn"
      @click.stop="emit('delete-task', task.id)"
    >
      Eliminar
    </button>
  </li>
</template>
  
<script setup lang="ts">
  import type { Task } from "../types.ts";
  
  const props = defineProps<{
    task: Task
  }>();

  const emit = defineEmits<{
    "toggle-task": [id:number],
    "delete-task": [id: number]
  }>();
</script>