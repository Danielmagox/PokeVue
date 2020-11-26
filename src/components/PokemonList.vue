<template>
  <div class="generation">
    <h1>Generación: {{ generation }}</h1>
    <PokeCard
      :index="index + pokeWiki[generation] - 1"
      v-for="index in 10"
      :key="index + pokeWiki[generation] - 1"
    />
  </div>
</template>

<script>
import PokeCard from "./PokeCard.vue";

const MIN_GEN = 1;
const MAX_GEN = 8;

export default {
  name: "PokemonList",
  props: {
    generation: {
      type: Number,
      required: true,
      validator: (v) => v >= MIN_GEN && v <= MAX_GEN,
    },
  },
  components: {
    PokeCard,
  },
  data() {
    return {
      pokeWiki: {
        1: 1,
        2: 152,
        3: 253,
        4: 389,
        5: 496,
        6: 652,
        7: 724,
        8: 810,
      },
    };
  },
};
</script>

<style>
</style>
