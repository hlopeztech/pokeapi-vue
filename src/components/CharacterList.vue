<script>
import { ref } from "vue";

// fetch all pokemon from pokeapi.co

const pokemon = ref([]);

const fetchPokemon = async () => {
  const response = await fetch("https://pokeapi.co/api/v2/pokemon?limit=100000000");
  const data = await response.json();
    pokemon.value = data.results;
};

fetchPokemon();

export default {
    name: "CharacterList",
    setup() {
        return {
            pokemon
        };
    }
};

</script>

<template>
  <div>
    <ul>
        <li v-for="(pokemon, index) in pokemon" :key="index">
            {{ pokemon.name }}
        </li>
    </ul>
  </div>
</template>

<style scope>
li {
  list-style: none;
}
</style>
