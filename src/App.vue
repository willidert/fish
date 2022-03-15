<template>
  <h1 class="text-3xl font-bold underline">Hello world!</h1>
  <div class="container mx-auto px-4">
    <div class="grid grid-cols-4 gap-4">
      <div v-for="pokemon in pokemons" :key="pokemon.name">
        <Pokemon :pokemon_id="getId(pokemon)"></Pokemon>
      </div>
    </div>
  </div>
  <a :href="previous">Anterior</a>
  <a :href="next">Próxima</a>
</template>

<script>
import Pokemon from "./components/Pokemon.vue";
export default {
  data() {
    return {
      pokemons: [],
      previous: null,
      next: null,
    };
  },
  beforeMount() {
    this.getPokemons();
  },
  methods: {
    getPokemons() {
      fetch("https://pokeapi.co/api/v2/pokemon/")
        .then((res) => res.json())
        .then((res) => {
          this.pokemons = res.results;
        });
    },
    getId(pokemon) {
      return pokemon.url.split("/")[6];
    },
  },
  components: { Pokemon },
};
</script>

<style></style>
