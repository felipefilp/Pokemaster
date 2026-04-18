<script setup>
import { onMounted, reactive, ref, computed } from "vue";
import ListPokemons from "@/components/ListPokemons.vue";
import CardPokemonSelected from "@/components/CardPokemonSelected.vue";

let pokemons = reactive(ref());
onMounted(() => {
  fetch("https://pokeapi.co/api/v2/pokemon?limit=100000&offset=0")
    .then((res) => res.json())
    .then((res) => (pokemons.value = res.results));
});

const pokemonsFiltered = computed(() => {
  if (pokemons.value && searchPokemonField.value) {
    return pokemons.value.filter((pokemon) =>
      pokemon.name
        .toLowerCase()
        .includes(searchPokemonField.value.toLowerCase()),
    );
  }
  return pokemons.value;
});

let pokemonSelected = reactive(ref());
let searchPokemonField = ref("");
let loading = ref(false);
let urlBase = ref(
  "https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/",
);

const pesquisarPokemon = async (url) => {
  loading.value = true;
  await fetch(url)
    .then((res) => res.json())
    .then((res) => (pokemonSelected.value = res))
    .catch((err) => alert(err))
    .finally(() => {
      loading.value = false;
    });
  console.log(pokemonSelected.value);
};
</script>

<template>
  <main>
    <div class="container">
      <div class="row">
        <div class="col-sm-12 col-md-6 mt-3">
          <CardPokemonSelected
            :name="pokemonSelected?.name"
            :height="pokemonSelected?.height"
            :xp="pokemonSelected?.base_experience"
            :urlImg="pokemonSelected?.sprites.other.dream_world.front_default"
            :loading="loading"
          />
        </div>
        <div class="col-sm-12 col-md-6 mt-3">
          <div class="card card-list">
            <div class="card-body row">
              <div class="mb-3">
                <label hidden for="searchPokemonField" class="form-label"
                  >Pesquisar</label
                >
                <input
                  v-model="searchPokemonField"
                  type="text"
                  class="form-control"
                  id="searchPokemonField"
                  placeholder="Pokemon"
                />
              </div>
              <ListPokemons
                v-for="pokemon in pokemonsFiltered"
                :key="pokemon.name"
                :name="pokemon.name"
                :urlSvg="urlBase + pokemon.url.split('/')[6] + '.svg'"
                @click="pesquisarPokemon(pokemon.url)"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
.card-list {
  overflow-y: scroll;
  overflow-x: hidden;
  max-height: 75vh;
}

@media (max-width: 768px) {
  .card-list {
    max-height: 40vh;
  }
}
</style>
