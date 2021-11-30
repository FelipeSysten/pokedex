<template>
    <div> 
         <div class="static">
                   <v-container>
      <v-row justify="space-around">
        <v-card >
          <v-img
            height="200px"
            src="https://tm.ibxk.com.br/2016/07/19/19183755227514.jpg?ims=1120x420"
          >
           </v-img>

           <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">
              Habilidades
            </div>

        
  
            <v-timeline
              align-top
              dense
            >
              <v-timeline-item
                v-for="(pokemon, i) in pokemon_info.abilities"
                :key="i"
                color="blue"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>{{ pokemon.ability.name }}</strong>
                  </div>
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>
  
       

        <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">
              Game Indices
            </div>

        
  
            <v-timeline
              align-top
              dense
            >
              <v-timeline-item
                v-for="(pokemon, i) in pokemon_info.game_indices"
                :key="i"
                color="red"
                small
              >
                <div>
                  <div class="font-weight-normal">
                    <strong>{{ pokemon.version.name  }} {{ pokemon.game_index  }} </strong> 
                  </div>
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>

   <v-card-text>
            <div class="font-weight-bold ml-8 mb-2">
              Sprites
            </div>

        
  
            <v-timeline
              align-top
              dense
            >
              <v-timeline-item
                v-for="(pokemon, i) in pokemon_info.sprites"
                :key="i"
                color="yellow"
                small
              >
                <div>
                    <div>
                        <v-img
            height="400px"
            :src=" pokemon "
          >
           </v-img>
                    </div>
                  <div class="font-weight-normal">
                    <strong>{{  }}</strong>
                  </div>
                </div>
              </v-timeline-item>
            </v-timeline>
          </v-card-text>


        </v-card>
      </v-row>
    </v-container>   
         </div>
        </div>
</template>
 
<script >
export default {
    props: {
        pokemon_info: []
    },
    data(){
        return {

        }

    },
    
}


</script>


<style scoped>

.static {
    position:relative ;
}

</style>