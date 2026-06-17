<template>
  <div class="ticks"></div>
   <section id="center">
  <h1>CRUD ToDo</h1>

  <!-- With emit you can create your own DOM events, here you have the functions to call -->
  <!-- When TaskFrom emit an event calling add-task, it execute the addTask() function that exist here in App.vue -->
  <TaskForm @add-task="addTask"/>

  <!-- :tasks="tasks" this is a prop(from parent to child) that sends the tasks variable to the TaskList component -->
  <TaskList
    :tasks="tasks"
    @toggle-task="toggleTaskDone"
    @delete-task="removeTask"
  />
  </section>
  <div class="ticks"></div>
  <section id="spacer"></section>
  <div class="ticks"></div> 
</template>

<script setup lang="ts">
// ref creates reactive variables, when a variable changes in the screen changes too
// watch, its objective is to watch changes in variables and when that happens it can execute code
import { ref, watch } from 'vue';
import TaskForm from './components/TaskForm.vue';
import TaskList from './components/TaskList.vue';
import type { Task } from "./types.ts";

// Beginning state of the tasks as an empty array
const tasks = ref<Task[]>([]);

// Load tasks from localStorage when starts
try {
  const raw = localStorage.getItem('tasks');
    if (raw) tasks.value = JSON.parse(raw) as Task[];
} catch (e) {
  console.error('Error parsing tasks from localStorage', e);
}

// Save in localStorage when the tasks change
watch(
  tasks,
  (newVal) => {
    try {
      localStorage.setItem('tasks', JSON.stringify(newVal));
    } catch (e) {
      console.error('Error saving tasks to localStorage', e);
    }
  },
  { deep: true }
);

// This function runs when the emitted event created in TaskForm is executed
function addTask(newTask: string){
  tasks.value.push({
    id: Date.now(),
    title: newTask,
    done: false
  });
}

function toggleTaskDone(id: number) {
  // Search the task with the id provided by the event
  const task = tasks.value.find(t => t.id === id);
  if (!task) return;

  // The task found changes its done status
  task.done = !task.done;

  // When a task is done it goes down
  tasks.value.sort((a, b) => Number(a.done) - Number(b.done));

}

function removeTask(id:number) {
  // All tasks that are not the one provided by the event are moved into a new array and the given task disappears
  tasks.value = tasks.value.filter(t => t.id !== id);
  }
</script>