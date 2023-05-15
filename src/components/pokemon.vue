<script setup>
    import {ref, onMounted} from 'vue'
    const pokemon = ref([])
       const fetchPokemon = onMounted(async () =>{
        let idPokemon = Math.floor(Math.random() * 1011) + 1;
        let url = 'https://pokeapi.co/api/v2/pokemon/'+idPokemon
      
        try{
            const res = await fetch(url)
            const pokemonData = await res.json();
            let abilityString = ''
          
            for(let i = 0; i < pokemonData.abilities.length; i++){
              abilityString += pokemonData.abilities[i].ability.name + ", "
            }
  
            const pokemonRes = {
              name: pokemonData.name,
              weight: pokemonData.weight/10,
              typeName: pokemonData.types[0].type.name,
              exp: pokemonData.base_experience,
              id: pokemonData.id,
              statName: pokemonData.stats[0].stat.name,
              statValue: pokemonData.stats[0].base_stat,
              height: pokemonData.height/10,
              img: pokemonData.sprites.other["official-artwork"].front_default,
              abilities: abilityString.slice(0,-2)
            }
            pokemon.value = pokemonRes
        }catch(error){
          fetchPokemon()
        }     
    })
</script>

<template>

    <div class="justify-content-center align-items-center" >
      <div class="row row-cols-1 row-cols-md-3 g-4">
        <!-- Tarjeta de un Pokémon -->
        <div class="col">
          <div class="card">
            <img :src="pokemon.img" class="card-img-top" alt="Nombre del Pokémon">
            <div class="card-body">
              <h5 class="card-title">{{ pokemon.name }}</h5>
              <p class="card-text">Tipo: {{ pokemon.typeName }}</p>
              <ul class="list-group list-group-flush">
                <li class="list-group-item">Número de la Pokédex: {{pokemon.id}}</li>
                <li class="list-group-item">Peso: {{ pokemon.weight }} Kg.</li>
                <li class="list-group-item">Altura: {{ pokemon.height}} M</li>
                <li class="list-group-item">Movimientos: {{ pokemon.abilities }}</li>
              </ul>
            </div>
            <button class="btn btn-primary align-items-center" @click="fetchPokemon">Nuevo</button>
          </div>
          
        </div>
        <!-- Fin de la tarjeta de un Pokémon -->
        <!-- Repetir la tarjeta de un Pokémon para cada Pokémon que quieras mostrar -->
      </div>
    </div>
</template>

<style>
  .imgPokemon{
    width: 80%;
    text-align: center;
  }
</style>
