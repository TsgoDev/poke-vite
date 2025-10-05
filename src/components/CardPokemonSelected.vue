<script setup>
const pokemon = defineProps(["name", "xp", "height", "img", "loading"]);

</script>

<template>
  <div class="card card-selected"
  :class="loading? '': 'animate__animated animate__fadeIn'"
  >
    
    <img
    v-if="pokemon.name"
    :src="pokemon.img"
    height="300"
    class="card-img-top pt-2"
    :alt="pokemon.name"
    />
    <img
    v-else
    src="../assets/egg_pokemon.svg"
    height="300"
    class="card-img-top pt-2"
    alt="???"
    />
    <div class="card-body">
      <h5 class="card-title text-center">{{ pokemon.name  || '???'}}</h5>
      <hr />
      <div class="row">
        <section class="col">
          <strong>XP:</strong>
          <span>{{ pokemon.xp  || '???'}}</span>
        </section>
        <section class="col">
          <strong>Altura:</strong>
          <span>{{ pokemon.height || '???' }}m</span>
        </section>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card-selected {
  height: 450px;
  background: rgb(72, 63, 251);
  background: radial-gradient(
    circle,
    rgba(220, 194, 106, 0.8) 0%,
    rgba(224, 0, 0, 0.8) 100%
  );
  
}
</style>