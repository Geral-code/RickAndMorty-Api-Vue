<template>

<!-- <button v-on:click="siguientePag()" class="btn btn-primary">Siguiente</button> -->
<div class="container mt-5 ">
    <h2 class="fst-italic text-center mb-5">Rick and Morty</h2>
    <div class="row" v-for="character of characters.results" :key="character.id">
      <div class="card mb-3 tarjeta" >
        <!-- Characters -->
        <router-link :to="`/characters/${character.id}`">Mas Info</router-link>
        <div class="row">
          <div class="col-md-4">
            <img v-bind:src="character.image" class="img-fluid rounded-start" alt="">
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h5 class="card-title"> {{character.name}} </h5>
              <p class="card-text">Lorem, ipsum  </p>
            </div>   
          </div>
        </div>
      </div>
    </div>
      


</div>
</template>

<script>
// @ is an alias to /src



export default {
  name: 'HomeView',
  components: {
    
  },
  data(){
    return {
      characters: [],
      charactersid: [],


    }
    
  },
  methods : {
    async obtenerPersonajes(){

      try {
        const data = await fetch (`https://rickandmortyapi.com/api/character`);
        const getcharacters = await data.json();
        this.characters = getcharacters;
        console.log(this.characters)




      } catch (error) {
        console.log(error);
        throw error;
        
      }

    },

    



  },
  created(){
    this.obtenerPersonajes();
  
  }


  
}

</script>


<style scoped>
.tarjeta {
  max-width: 540px;
  width: 45%;
  margin: 5px;
  
}


 


</style>
