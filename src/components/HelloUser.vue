<script setup lang="ts">
import { ref } from 'vue';

const name = ref("")
const userName = ref("usuario")

function greeting() {
  if (name.value.trim()) {
    userName.value = name.value
    name.value = ""
  }
}

</script>

<template>
  <section id="center">
    <div class="hero"></div>

    <h1>Hola, {{ userName }}</h1>

    <input type="text" v-model="name" placeholder="Escribe tu nombre">

    <button type="button" class="greet" @click="greeting">Saludar</button>

  </section>
  <div class="ticks"></div>
  <div class="ticks"></div>
  <section id="spacer"></section>
</template>
