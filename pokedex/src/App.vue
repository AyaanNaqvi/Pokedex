<script setup>
import { ref } from 'vue';
import './app.css'
import grassImg from '../../bgs/grassss.jpeg'
import rockImg from '../../bgs/rock.png'
import waterImg from '../../bgs/waterr.png'
import bugImg from '../../bgs/bug.png'
import electricImg from '../../bgs/electric.png'
import iceImg from '../../bgs/ice.jpg'
import fightingImg from '../../bgs/image.png'
import poisonImg from '../../bgs/poison.png'
import groundImg from '../../bgs/ground.png'
import flyingImg from '../../bgs/flying.png'
import fireImg from '../../bgs/fire.png'
import psychicImg from '../../bgs/psychic.png'
import normalImg from '../../bgs/normal.png'
import ghostImg from '../../bgs/ghost.png'
import dragonImg from '../../bgs/dragon.png'
import darkImg from '../../bgs/dark.png'
import steelImg from '../../bgs/steel.png'
import fairyImg from '../../bgs/fairy.png'
const pokedexOn = ref(false)
const pokemon= ref(null)
const movesscreen= ref(false)
const movesindex= ref(0)
const type = {
  normal: `url(${normalImg})`,
  fire: `url(${fireImg})`,
  water: `url(${waterImg})`,
  electric: `url(${electricImg})`,
  grass: `url(${grassImg})`,
  rock: `url(${rockImg})`,
  ice: `url(${iceImg})`,
  fighting: `url(${fightingImg})`,
  poison: `url(${poisonImg})`,
  ground: `url(${groundImg})`,
  flying: `url(${flyingImg})`,
  psychic: `url(${psychicImg})`,
  bug: `url(${bugImg})`,
  ghost: `url(${ghostImg})`,
  dragon: `url(${dragonImg})`,
  dark: `url(${darkImg})`,
  steel: `url(${steelImg})`,
  fairy: `url(${fairyImg})`
}
async function randompokemon(){
  const Id= Math.floor(Math.random()*1025)+1
  console.log(Id)
  const currentpokemon=await fetch(`https://pokeapi.co/api/v2/pokemon/${Id}`)
  const data= await currentpokemon.json();
  pokemon.value=data;
  console.log(pokemon.value);
const type= pokemon.value.types[0].type.name
console.log(type)


}
function togglePokedex(){
  pokedexOn.value = !pokedexOn.value
  console.log(pokedexOn.value)
}
function moveincrementer(){
  movesindex.value+=3;
  console.log("moves:", pokemon.value.moves)
}
function movesscreentoggle(){
  movesscreen.value=!movesscreen.value;
}


</script>

<template><div
class="pokedex" :class="pokedexOn ? 'pokedex-on' : 'pokedex-off'">
 <button @click="togglePokedex"
  style="background: transparent;
  border: transparent;
  border-radius: 90%;
  position: absolute;
bottom:27%;
left:27.5%;
  height: 8%;
  width: 4%;
  
  ">

  </button>

  <div v-if="pokedexOn">
<button @click="randompokemon"
      style="

  position: absolute;
   background: transparent;
  left: 31.4%;
  top: 74.5%;
  width: 8%;
  height: 7.5%;
  border: transparent;
  
">
 

</button><div v-if="movesscreen">

<div style="
background-color: gray;
position: absolute;
background-size: 100%;
top: 35.1%;
left: 29.9%;
border-radius: 10px;
width: 15.8%;
height: 22%;
border: 4px solid black;
z-index: 1000;

">
  
<div v-for="move in pokemon.moves.slice(movesindex,movesindex+3)"
style="font-size: 125%;
margin-bottom: 8%;
left: 10%;
margin-top: 8.5%;
">
  {{ move.move.name }}

</div>
</div>
</div>

<button @click="movesscreentoggle"
     style="

  position: absolute;
   background: transparent;
  right: 38.1%;
  top: 64.7%;
  width: 8%;
  height: 7.5%;
  border: transparent;
  font-size: 113%;
  
  
">

</button>

<button @click="moveincrementer"
style="
  position: absolute;
   background: transparent;
  left: 41.8%;
  top: 67.5%;
  width: 5%;
  height: 13%;
  border: transparent;">

</button>
<div v-if="pokemon"
class="screen"
:style="{background: pokemon? type[pokemon.types[0].type.name]:'gray'}">
  
  <img
  :src="pokemon.sprites.other['official-artwork'].front_default"
  style="
  width: 50%;
  position: absolute;
  left: 25%;
  top: 13%;
 
" >
<div>
    <h1
      style="
  width: 100%;
  position: absolute;
  left: 170%;
  top: 17%;
">
    {{pokemon.name}}
  </h1>
</div>
<div style="  position: absolute;
  left: 167%;
  top: 198%;
  ">
    <h1
      style="
    font-size: 16px;
    color: gainsboro;

">
    {{pokemon.types[0].type.name}}
  </h1>
</div>
<div style=" position: absolute;
  left: 220%;
  top: 198%;">
    <h1
      style="
    font-size: 16px;
     color: gainsboro;

 
  
">
    HP:{{ pokemon.stats[0].base_stat }}
  </h1>
<div style="position: absolute;
top: 68.1%;
right: 570.9%;">

</div>
  <div style="position: absolute;
top: 88.1%;
right: 460.9%;
    width: 150%;
    
   
  ">
  <h1
  style="
  white-space: nowrap;   
   
    font-size: 16px; 
    ">
     

  </h1>
  </div>
</div>
</div>
</div>
</div>

</template>

<style scoped></style>
