<template>
  <div id="app">
    <pokedex-main />
    <search-pokemon @display-pokemon-data="displayPokemonData"/>
    <pokemon-data :searchedPokemon="searchedPokemon"/>

  </div>
</template>

<script>
import PokedexMain from './components/PokedexMain.vue';
import PokemonData from './components/PokemonData.vue';
import SearchPokemon from './components/SearchPokemon.vue';


export default {
  name: 'app',
  components: {
    PokedexMain, PokemonData, SearchPokemon
  },
  data() {
    return {
      searchedPokemon: { },
    }
  },
  methods: {
    displayPokemonData(pokeObject) {
      
      this.searchedPokemon = pokeObject;

    },
  },
}
</script>

<style>

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
        background: linear-gradient(to top, #c9d6ff, #6e83d1) no-repeat center center fixed;


}
#app {
  text-align: center;
  font-family: Avenir, Helvetica, Arial, sans-serif; 

}
</style>
