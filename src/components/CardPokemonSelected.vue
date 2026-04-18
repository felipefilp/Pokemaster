<script setup>
const pokemon = defineProps(["name", "xp", "height", "urlImg", "loading"]);
</script>

<template>
  <div>
    <div
      class="card CardPokemonSelected"
      :class="loading ? '' : 'animate__animated animate__fadeInRight'"
    >
      <img
        v-if="pokemon.name"
        :src="pokemon.urlImg"
        class="card-img-top pt-2"
        :alt="pokemon.name"
        height="250"
      />
      <img
        v-else
        src="../assets/pokemon (1).png"
        class="card-img-top pt-2"
        alt="..."
        height="250"
      />
      <div class="card-body">
        <h5 class="card-title text-center">{{ pokemon.name || "???" }}</h5>
        <hr />
        <div class="row text-center">
          <section class="col">
            <strong>XP: </strong>
            <span>{{ pokemon.xp }}</span>
          </section>
          <section class="col">
            <strong>Altura: </strong>
            <span>{{ pokemon.height }}</span>
          </section>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card-img-top {
  object-fit: contain;
}

.CardPokemonSelected {
  height: 75vh;
  background: #020024;
  background: radial-gradient(
    circle,
    rgba(2, 0, 36, 0.59) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}
</style>
