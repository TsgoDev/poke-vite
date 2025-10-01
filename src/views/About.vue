<script setup>
import { ref } from "vue";

const description = ref("Esta é a página sobre o projeto.");
</script>

<template>
  <div class="about">
    <h1>Sobre</h1>
    <p>{{ description }}</p>
    <p>PokeVite é uma aplicação desenvolvida com Vue 3, Vite e Bootstrap.</p>
  </div>
</template>

