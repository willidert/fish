<template>
  <div class="container text-center">
    <img
      class="mx-auto"
      :src="((pokemon || {}).sprites || {}).front_default"
      :alt="pokemon.name"
    />
    <div class="px-2 py-2">
      <span
        class="px-2 text-xs leading-5 font-semibold rounded-full bg-green-100 text-green-800"
        v-for="type in pokemon.types"
        >{{ ((type || {}).type || {}).name }}</span
      >
    </div>
    <div class="grid grid-cols-2">
      <span>Weight: {{ pokemon.weight }}</span>
      <span>Height: {{ pokemon.height }}</span>
    </div>
    <span class="capitalize">{{ pokemon.name }}</span>
  </div>
</template>

<script>
export default {
  props: ["pokemon_id"],
  data() {
    return {
      pokemon: {},
      image: {},
    };
  },
  mounted() {
    this.getPokemonData(this.pokemon_id);
  },
  methods: {
    async getPokemonData() {
      fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemon_id}`)
        .then((res) => res.json())
        .then(
          (res) =>
            (this.pokemon = (({
              name,
              id,
              height,
              weight,
              sprites,
              types,
            }) => ({ name, id, height, weight, sprites, types }))(res))
        )
        .catch((err) => console.log(err));
    },
  },
};
</script>

<style></style>
