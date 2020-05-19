<template>
    <div class="sign-in">

        <img src="../assets/pokedex.png"   alt="pokemon-font" border="0">
    </div>    
</template>

<script>
export default {
    name: 'pokedex-main',
}
</script>

<style scoped>
img {
    margin-top: 60px;
    width: 250px;
    
}

@media screen and (min-width: 640px) {
   img {
        margin-top: 80px;
        width: auto;
   } 
}
</style>