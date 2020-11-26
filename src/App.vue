<template>
  <div>
    <input type="number" v-model="generation" />
    <PokemonList :generation="generation" />
  </div>
</template>

<script>
/* eslint-disable */

import PokemonList from "./components/PokemonList.vue";

export default {
  name: "App",
  components: {
    PokemonList,
  },
  data() {
    return {
      generation: 1,
    };
  },
};
</script>

<style>
</style>
