<template>
    <div class="search">
        <form @submit.prevent="getPokemon">
            <input v-model="pokemonName" class="search-bar" type="search" list="pokemonNames" placeholder="Enter a Pokemon name (Gen I-IV)" />

            <datalist id="pokemonNames">
                <option v-for="item in allPokemonNames" :key="item" style="background-color: green">{{item}}</option>
            </datalist>
            <input class="search-btn" type="submit" value="I Choose You!"/> 
        </form>

    </div>
</template>

<script>

export default {
    name: 'search-pokemon',
    data() {
        return {
            pokemonName: '',
            allPokemonNames: [],
        };
    },
    created() {
        this.getPokemonNames();
    },
    methods: {
        async getPokemon() {

            if ( isNaN(this.pokemonName) ) {

                try {
                    let response = await fetch(`https://pokeapi.co/api/v2/pokemon/${this.pokemonName.toLowerCase()}`);
                    let result = await response.json();
                    this.$emit('display-pokemon-data', result); 

                } catch(error) {
                    alert('No results found. Try another search');
                }
            } else {
                alert('No results found. Try another search');
            }
        },
        async getPokemonNames() {
            const response = await fetch('https://pokeapi.co/api/v2/pokemon?limit=493');
            const result = await response.json();
            let pokemonArry = result.results;
            let pokemonNameArry = [];

            pokemonArry.forEach(element => {
                pokemonNameArry.push(element.name);
            });

            this.allPokemonNames = pokemonNameArry;

        },
    },
}

</script>

<style scoped>


.search {
    margin-top: 20px;
}

.search-bar {
    width: 300px;
    padding: 6px 10px;
    margin: 8px 0;
    font-size: 15px;
    border: 2.5px solid #ccc;
    border-radius: 5px;
    outline: none;
    transition: 0.5s;
}

.search-bar:focus {
    border: 2.5px solid #3fa2e4;
}

.search-btn {
    display: block;
    margin: 10px auto 0 auto;
    border-radius: 5px;
    width: 150px;
    height: 30px;
    background-color: #e43f5a;
    color: white;
    outline: none;
    transition: 0.5s;
    border: none;
}

.search-btn:hover {
    cursor: pointer;
    background-color: #b80321;
    transform: translateY(-5px);


}
@media screen and (min-width: 640px) {

    .search {
        margin-top: 50px;
    }

    .search-bar {
        width: 50%;
        padding: 12px 20px;
        font-size: 30px;

    }

    .search-btn {

        width: 150px;
        height: 45px;
        font-size: 18px;
    }
}
</style>