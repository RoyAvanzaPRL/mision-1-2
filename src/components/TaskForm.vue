<template>
  <!-- When the form is submitted, run the formSubmit() function and skip the usual behavior of the form,
  because normally when you submit a form, the page refreshes, and prevent blocks this -->
  <form @submit.prevent="formSubmit">
    <!-- v-model="newTask" creates a connection between the input and the newTask variable -->
    <input
    type="text"
    name="newTask"
    v-model="newTask"
    placeholder="Añade una nueva tarea">
    <button>Añadir</button>
  </form>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const newTask = ref("")

// Send the "addTask" event to App.vue, with the new task as an argument
const emit = defineEmits<{
  addTask: [newTask: string]
}>();


// When you click the button
function formSubmit(){
  if (newTask.value.trim()) {
    emit("addTask", newTask.value.trim())
    newTask.value = "";
  }
}
</script>