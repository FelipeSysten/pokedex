<template>
  <div>
    <div class="center">
      <img src="../assets/pokedex.png">

      </div>
       <div class="content">
    <div class="flex">
      <div class="flex-col">
   
  
           <div v-for="(data, index) in pokemons" :key="index">
              <v-app id="inspire"  class="size">
    <v-card
      class="mx-auto"
      max-width="344"
    >
      <v-img
      class="pointer"
        :src="data.url"
        height="200px"
        @click="send_info(data)"
      ></v-img>
  
      <v-card-title>
        {{ data.name }}
      </v-card-title>
  
      <v-card-subtitle>
        1,000 miles of wonder
      </v-card-subtitle>
  
      <v-card-actions>
        <v-btn
          color="orange lighten-2"
          text
        >
          Explore
        </v-btn>
  
        <v-spacer></v-spacer>
  
        <v-btn
          icon
          @click="show = !show"
        >
          <v-icon>{{ show ? 'mdi-chevron-up' : 'mdi-chevron-down' }}</v-icon>
        </v-btn>
      </v-card-actions>
  
      <v-expand-transition>
        <div v-show="show">
          <v-divider></v-divider>
  
          <v-card-text>
            I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
          </v-card-text>
        </div>
      </v-expand-transition>
    </v-card>
  </v-app>
           </div>
      </div>
      <div class="flex-col">
        <PokemonInfo :pokemon_info="selected_pokemon"></PokemonInfo>
         
      </div>
    </div>
      </div>
    </div>

</template>



<script>

import axios from "axios";
import PokemonInfo from '../components/PokemonInfo.vue';

  export default {
    components: {PokemonInfo} ,
   data(){
     return {
   show: false,
   isActive: true,
  pokemons: [],
  selected_pokemon: [],
  };
     },
     created() {
       let instance = this;

       for (let i = 0; i <= 10; i++) {
      axios
       .get(`https://pokeapi.co/api/v2/pokemon/${i + 1}`)
       .then((response) => {
         console.log(response);
           let pokemon = {
            abilities: response.data.abilities,
            sprites: response.data.sprites,
            game_indices: response.data.game_indices,
            name: response.data.name,
            url: response.data.sprites.front_default,
           };
         
        
         instance.pokemons.push(pokemon);
       })
       .catch((err) =>{
         console.log(err);
       });

       }
     

      //console.log(this.pokenons);

     },
  methods: {
    send_info(pokemon_info){
      this.selected_pokemon = pokemon_info
    }
  }

  };
</script>

<style scoped>
.center{
  text-align: center;
  margin-top: 1%;
 
}


.size{
  height: 600px;
}

.pointer{
  cursor: pointer;
}

.flex {
  display: flex;
  
}

.flex-col {
  flex: 1;
  background-color: burlywood;
  
}

.active{
  color: blue;
}
</style>
