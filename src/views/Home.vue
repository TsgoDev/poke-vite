<script setup>
import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "../components/ListPokemons.vue";
import CardPokemonSelected from "../components/CardPokemonSelected.vue";

let urlBaseSvg = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/"
);
let pokemons = reactive(ref());
let searchPokemonField = ref("");
let pokemonSelected = reactive(ref());
let loading = ref(false);

// Fetch api
onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=150&offset=0")
    .then((res) => res.json())
    .then((res) => (pokemons.value = res.results));
});

// Método pesquisar
const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter((pokemon) =>
      pokemon.name
        .toLowerCase()
        .includes(searchPokemonField.value.toLowerCase())
    );
  }
  return pokemons.value;
});

//Método selecione pokemon
const selectPokemon = async (pokemon) => {
  loading.value = true;
  await fetch(pokemon.url)
    .then((res) => res.json())
    .then((res) => (pokemonSelected.value = res))
    .catch((err) => alert(err))
    .finally(() => (loading.value = false));

  console.log(pokemonSelected.value);
};
</script>

<template>
  <main>
    <div class="container-fluid text-body-secondary">
      <div class="row g-3 mt-2">
        <div class="col-12 col-lg-6">
          <CardPokemonSelected
            :name="pokemonSelected?.name"
            :xp="pokemonSelected?.base_experience"
            :height="pokemonSelected?.height"
            :img="pokemonSelected?.sprites?.other?.dream_world?.front_default"
            :loading="loading"
          />
        </div>

        <div class="col-12 col-lg-6">
          <div class="card card-list">
            <div class="card-body">
              <div class="form-group mb-3">
                <input
                  v-model="searchPokemonField"
                  type="text"
                  class="form-control"
                  id="searchPokemonField"
                  aria-describedby="emailHelp"
                  placeholder="Buscar..."
                />
              </div>
              <div class="row g-2">
                <ListPokemons
                  v-for="pokemon in pokemonsFiltered"
                  :key="pokemon.name"
                  :name="pokemon.name"
                  :urlBaseSvg="urlBaseSvg + pokemon.url.split('/')[6] + '.svg'"
                  @click="selectPokemon(pokemon)"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card-list {
  max-height: 450px;
  overflow-y: auto;
  overflow-x: hidden;
}

/* Responsividade para mobile */
@media (max-width: 768px) {
  .card-list {
    max-height: 350px;
    margin-bottom: 80px; /* Espaço para o footer */
  }

  .container-fluid {
    padding: 0 15px;
  }

  .row.g-3 {
    margin-top: 1rem !important;
  }
}

@media (max-width: 576px) {
  .card-list {
    max-height: 300px;
  }
}
</style>
