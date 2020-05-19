<template>
    <div class="pokemon-data">
        <div  v-if="Object.keys(searchedPokemon).length != 0">
            <img :src="displayPokemonImage(searchedPokemon)">
            <p id="pokemon-name"> {{ searchedPokemon.name }}</p>
            <p class="pokemon-info">#{{ searchedPokemon.id }}</p>
            <p v-for="types in searchedPokemon.types" :key="types.type.name" class="pokemon-info"> {{ types.type.name}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name: 'pokemon-data',
    props: {
        searchedPokemon: Object,
    },
    methods: {
        displayPokemonImage(searchedPokemon) {

            return `https://pokeres.bastionbot.org/images/pokemon/${searchedPokemon.id}.png`;

        },
    },
    
}

</script>

<style scoped>


img {
    height: 250px;
    width: 250px;
    margin: 15px 15px 0 15px;
}

span{
    text-indent: 80px;
}

.pokemon-info {
    margin-bottom: 10px;
}
@media screen and (min-width: 640px) {

    .pokemon-info {
        font-size: 25px;
    }

    #pokemon-name {
        font-size: 35px;
    }


}

</style>