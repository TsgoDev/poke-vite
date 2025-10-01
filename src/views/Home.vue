<script setup>
import { ref } from "vue";

const message = ref("Bem-vindo à página Home!");
</script>

<template>
  <div class="home">
    <h1>{{ message }}</h1>
    <p>Esta é a página inicial da aplicação PokeVite.</p>
  </div>
</template>


