<template>
  <h1 class="text-3xl text-center py-4">Pokédex</h1>
  <div class="px-4 py-5 bg-white sm:p-6 text-center px-auto">
    <label for="search" class="block text-sm font-medium text-gray-700"
      >Search a pokémon...</label
    >
    <input
      type="text"
      name="search"
      id="search"
      class="mt-1 focus:ring-indigo-500 focus:border-indigo-500 block w-full shadow-sm sm:text-sm border-gray-300 rounded-md"
      v-model="search"
      placeholder="charmander..."
    />
  </div>

  <div class="container mx-auto px-4">
    <div v-for="pokemon in pokemons" :key="pokemon.name">
      <Pokemon
        v-if="search == pokemon.name"
        :pokemon_id="getId(pokemon)"
      ></Pokemon>
    </div>
  </div>
</template>

<script>
import Pokemon from "./components/Pokemon.vue";
export default {
  data() {
    return {
      pokemons: [],
      previous: null,
      next: null,
      search: null,
    };
  },
  beforeMount() {
    this.getPokemons();
  },
  methods: {
    getPokemons() {
      fetch("https://pokeapi.co/api/v2/pokemon/?limit=60")
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
