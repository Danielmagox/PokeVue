
<template>
  <div class="container">
    <h1>{{ name }}</h1>
    <img :src="image" :alt="name" />
    <span class="weight">{{ weight }}</span>
    <span class="height">{{ height }}</span>
    <span class="type" v-for="(type, index) in types" :key="index">
      {{ type.type.name }}
    </span>
  </div>
</template>

<script>
/* eslint-disable */
const URL = "https://pokeapi.co/api/v2/pokemon/";

const MIN_PKM = 1;
const MAX_PKM = 151;

export default {
  name: "PokeCard",
  props: {
    index: {
      type: Number,
      required: true,
      validator: (v) => v >= MIN_PKM && v <= MAX_PKM,
    },
  },
  data() {
    return {
      title: "Hola Mundo",
      name: "",
      weight: 0,
      height: 0,
      image: "",
      types: [],
    };
  },
  methods: {
    fetchData() {
      return fetch(URL + this.index)
        .then((response) => response.json())
        .then((data) => data);
    },
  },

  mounted() {
    this.fetchData().then((data) => {
      console.log(data);
      this.name = data.name;
      this.weight = data.weight;
      this.height = data.height;
      this.image =
        data.sprites.versions["generation-iv"].platinum.front_default;
      this.types = data.types;
    });
  },
};
</script>

<style>
h1 {
  background-color: green;
  color: white;
  border: 1px solid black;
  box-shadow: 2px 2px 5px grey;
  border-radius: 5px;
  width: 75px;
  font-size: 1em;
  text-transform: capitalize;
  margin: 3px;
}
.weight {
  background-color: red;
  color: white;
  padding: 0 10px;
}
.height {
  background-color: blue;
  color: white;
  padding: 0 10px;
}
.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 128px;
  border: 1px solid black;
  padding: 20px;
  box-shadow: 0 0 5px #666 inset;
}
img {
  width: 80px;
}
</style>
