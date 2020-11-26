<template>
  <div>
    <PokeCard :index="1" />
    <PokeCard :index="4" />
    <PokeCard :index="151" />
    <PokeCard :index="92" />
  </div>
</template>

<script>
/* eslint-disable */

import PokeCard from "./components/PokeCard.vue";

export default {
  name: "App",
  components: {
    PokeCard,
  },
};
</script>

<style>
</style>
