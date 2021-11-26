<template>
    <div> 
         <div class="static">
                   <v-container>
      <v-row justify="space-around">
        <v-card >
          <v-img
            height="200px"
            src="https://cdn.pixabay.com/photo/2020/07/12/07/47/bee-5396362_1280.jpg"
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
            height="200px"
            src="https://cdn.pixabay.com/photo/2020/07/12/07/47/bee-5396362_1280.jpg"
          >
           </v-img>
                    </div>
                  <div class="font-weight-normal">
                    <strong>{{ pokemon }}</strong>
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
messages: [
      {
        from: 'You',
        message: `Sure, I'll see you later.`,
        time: '10:42am',
        color: 'deep-purple lighten-1',
      },
      {
        from: 'John Doe',
        message: 'Yeah, sure. Does 1:00pm work?',
        time: '10:37am',
        color: 'green',
      },
      {
        from: 'You',
        message: 'Did you still want to grab lunch today?',
        time: '9:47am',
        color: 'deep-purple lighten-1',
      },
    ],
    

        }

    },
    
}


</script>


<style scoped>

.static {
    position: inherit;
}

</style>