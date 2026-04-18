<script setup>
const pokemon = defineProps(["name", "urlSvg"]);
</script>

<template>
  <div class="col-4">
    <div class="card cardListPokemon p-2 mb-3">
      <img
        :src="pokemon.urlSvg"
        class="card-img-top"
        alt="Imagem"
        height="80"
      />
      <p class="text-center">{{ pokemon.name }}</p>
    </div>
  </div>
</template>

<style scoped>
.cardListPokemon {
  background: #020024;
  background: radial-gradient(
    circle,
    rgba(2, 0, 36, 0.59) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
  cursor: pointer;
}

.cardListPokemon:hover {
  background: #22c1c3;
  background: linear-gradient(
    0deg,
    rgba(34, 193, 195, 0.48) 0%,
    rgba(253, 187, 45, 1) 100%
  );
}
</style>
