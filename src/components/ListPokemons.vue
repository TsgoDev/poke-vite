<script setup>
const pokemon = defineProps(["name", "urlBaseSvg"]);
</script>
<template>
  <div class="col-6 col-sm-4 col-md-3 p-1">
    <div class="card p-2 mb-2 cardListPokemon">
      <p class="text-center mb-1 small">{{ pokemon.name }}</p>
      <img :src="urlBaseSvg" class="card-img-top" alt="..." height="60" />
    </div>
  </div>
</template>
<style scoped>
.cardListPokemon {
  background: rgb(72, 63, 251);
  background: radial-gradient(
    circle,
    rgba(94, 87, 232, 0.5) 0%,
    rgba(70, 252, 244, 0.4) 100%
  );
  cursor: pointer;
  transition: transform 0.2s ease;
  min-height: 100px;
}

.cardListPokemon:hover {
  background: rgb(72, 63, 251);
  background: radial-gradient(
    circle,
    rgba(72, 63, 251, 0.6) 0%,
    rgba(70, 252, 244, 0.4) 100%
  );
  transform: translateY(-2px);
}

.cardListPokemon img:hover {
  padding: 0.1rem;
}

/* Responsividade para mobile */
@media (max-width: 576px) {
  .cardListPokemon {
    min-height: 80px;
  }

  .cardListPokemon p {
    font-size: 0.75rem;
  }
}
</style>
