<template>
  <div>
    <div class="center">
    <img src="https://raw.githubusercontent.com/sleduardo20/pokedex/0671af442dff1d8f7141e49eb83b438885bbc9e9/public/img/logo.svg">
   </div>
   <div class="content">
           <div v-for="i in 5" :key="i">
              <v-app id="inspire"  class="size">
    <v-card
      class="mx-auto"
      max-width="344"
    >
      <v-img
      class="pointer"
        src="https://cdn.vuetifyjs.com/images/cards/sunshine.jpg"
        height="200px"
      ></v-img>
  
      <v-card-title>
        Top western road trips
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
    </div>

</template>

<script>

  export default {
   data(){
     return {
   show: false,
   };
     },
  };
</script>

<style scoped>
.center{
  text-align: center;
  margin-top: 1%;
  padding: 100px;

}

.size{
  height: 600px;
}

.pointer{
  cursor: pointer;
}
</style>
