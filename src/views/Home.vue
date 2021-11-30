
<template>

  <div>
    <div class="center">
      <img src="../assets/pokedex.png">
      <div>
         
         <div>
            
 <v-toolbar
      dark
      color="teal"
    >
      
      <v-toolbar-title>Digite o nome, especie, tipo ou ID</v-toolbar-title  >

      <v-autocomplete 
        v-model="searchPokemons"
        :items= "pokemonsFiltered"
        cache-items
        class="mx-4"
        flat
        hide-no-data
        hide-details
        label="Buscar Pokemon"
        solo-inverted
      ></v-autocomplete>
      <div >
      <button >Buscar</button>
   </div>
    </v-toolbar>
    </div>
      
      </div>
      </div>
       <div class="content">
    <div class="flex">
      <div class="flex-col">
  
  
           <div v-for="(data, i) in movies" :key="i">
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
        Sua Lista de Pokemons 
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
            A febre do Pokémon é real e está sendo disseminada por todo o planeta. Se você foi contagiado por essa loucura saudável, saiba quais os pokémons mais raros de achar!
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
         <div v-infinite-scroll="loadMore" infinite-scroll-disabled="busy" infinite-scroll-distance="10">
  ...
</div>
    </div>

</template>



<script>

import axios from "axios";
import PokemonInfo from '../components/PokemonInfo.vue';
//import Header from '../components/Header.vue';


  export default {
    components: {PokemonInfo} ,
    
   data(){
     return {
       movies:[],
   show: false,
   isActive: true,
  pokemons: [],
  selected_pokemon: [],
  search:"",
  loading: true,
    nextItem: 1,
    items: [],
    filteredPokemons:[],
    page: 0,
     data : [ ] , 
    busy : false ,
    count: 0,
    limit: 30,
 
  };
     },
     created() {
      
      let instance = this;
       window.addEventListener("scroll",()=>{

         let scrollTop=document.documentElement.scrollTop;
         let scrollHeight=document.documentElement.scrollHeight;
         let clientHeight=document.documentElement.clientHeight;

         if(scrollTop+clientHeight>=scrollHeight -10){
            instance.page++;

         }
         

       })

       
       
         
      this.busy = true;

      for (let i = 0, j = this.limit; i < j; i++) {
      axios
       .get(`https://pokeapi.co/api/v2/pokemon/${1 + i}`)
       .then((response) => {
        // console.log(response);
           let pokemon = {
            abilities: response.data.abilities,
            sprites: response.data.sprites,
            game_indices: response.data.game_indices,
            name: response.data.name,
            url: response.data.sprites.front_default,
            id: response.data.id,
            species: response.data.species,
            types: response.data.types,
            filteredPokemons: response.data.results,
           };

       this.busy = false;
         
         instance.movies.push(pokemon);
         instance.pokemons.push(pokemon);
       })
       .catch((err) =>{
          this.busy = false;
         console.log(err);
       });

       
      }

      //console.log(this.pokenons);

     },

    computed: {
      pokemonsFiltered() {
        let valores = [];

      valores = this.pokemons.filter((pokemon) => {
           let res = new RegExp(this.search)
      return res.test(pokemon.name.toLowerCase().indexOf(this.search.toLowerCase()) > -1 
      );
      });
      
      return valores;
  
      }
     
    
    },

  
    

  methods: {
    send_info(pokemon_info){
      this.selected_pokemon = pokemon_info
    }
  },

  searchPokemons: function() {
      this.filteredPokemons = this.pokemons;
      if(this.search == '' || this.search == ' ') {
        this.filteredPokemons = this.pokemons;
      } else {
        this.filteredPokemons = this.pokemons.filter((pokemon) => pokemon.name == this.search);
      }
    },

    next(){
      if(!this.nextItem) return

      fetch(this.nextItem).then(res => res.json()).then(data =>{
        this.pokemons.push(...data.results)
        this.nextItem = data.next;
      })
    },

      loadMore : function ( )  { 
      this . busy  =  true ;

      setTimeout ( ( )  =>  { 
        for ( var  i  =  0,  j  =  10;  i  <  j;  i++ )  { 
          this.data.push ( {  name: this.count++  } ) ; 
        } 
        this.busy  =  false ; 
      } ,  1000 ) ; 
      },
      

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
  background-color: teal;
  
}

.active{
  color: blue;
}
</style>
