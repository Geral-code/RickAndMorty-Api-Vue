<template>

 

<div class=" container mt-5  ">

<div class= "d-flex justify-content-center"> 
  <h1 class=" text-center mb-5 ">Rick and Morty</h1>
  </div>

  <div class= "titulo d-flex justify-content-center"> 
    <div class="btn-container">
		<button class="btn btn-secondary btn-lg" v-on:click="prevPagina">PREV</button>
		<button class= "btn btn-secondary btn-lg" v-on:click="nextPagina">NEXT</button>
	</div>
    
 
  </div>

    <!-- ROW CARDS -->
    <div class="row mt-4" >
      <!-- CARDS -->
       <div class="  col-md-6 col-lg-6 mb-5  " v-for="character of characters.results" :key="character.id">
           <div class="card shadow  p-3 mb-5 text-white rounded mb-3  ">
             <router-link class="stretched-link" :to="`/characters/${character.id}`"></router-link>
        <!-- Characters -->
        
        <div class="row">
          <div class="col-md-4">
            <img v-bind:src="character.image" class="img-fluid rounded-start" alt="">
          </div>
          <div class="col-md-8">
            <div class="card-body">
              <h5 class="card-title"> {{ character.name }} </h5>            
            <div v-if="character.status === 'Alive'" class="isAlive">
              {{ character.status }}
            </div>
            <div v-if="character.status === 'Dead'" class="isDead">
              {{ character.status }}
            </div>
            <div v-if="character.status === 'unknown'" class="isUnknown">
              {{ character.status }}
            </div>
              <p class="card-text"> <span> Ubicación: </span> <br> {{ character.location.name }} </p>
            </div>   
          </div>
        </div>
      </div>
    </div> 
    </div>
    <div class= "titulo d-flex justify-content-center"> 
    <div class="btn-container">
		<button class="btn btn-secondary btn-lg mb-3" v-on:click="prevPagina">PREV</button>
		<button class= "btn btn-secondary btn-lg mb-3 " v-on:click="nextPagina">NEXT</button>
	</div>
    
 
  </div>



</div>
</template>

<script>
// @ is an alias to /src



export default {
  name: 'Homeview',
  components: {

  },
  
  data(){
    return {
      characters: [],
      charactersid: [],
      events: "",
      page: 1
   
       
  
    }
    
  },
  methods : {
    async obtenerPersonajes(){  

      try {
        const data = await fetch (`https://rickandmortyapi.com/api/character`);
        const getCharacters = await data.json();
        this.characters = getCharacters;
        console.log(this.characters)                 
        // console.log(this.characters.info.pages)
        
    
      } catch (error) {
        console.log(error);
        throw error;
        
      }

    },
    async nextPagina(pag){  

      this.page;
      if(pag) {
        if (this.page <=41){
          this.page++;
          const url = (`https://rickandmortyapi.com/api/character?page=${this.page}`);
          console.log(this.page);
          console.log(url);

           try {
        const data = await fetch (url);
        const getCharacters = await data.json();
        this.characters = getCharacters;
        console.log(this.characters)                 
        
        
    
      } catch (error) {
        console.log(error);
        throw error;
        
      }
      }else{
        this.page = 42;
      }
        
      }


     

    },
    async prevPagina(pag) {
      this.page;
      if (this.page >=2) {
        this.page--;
        const url = (`https://rickandmortyapi.com/api/character?page=${this.page}`);
        console.log(this.page);
        console.log(url);
        try {
          const data = await fetch (url);
          const getCharacters = await data.json();
          this.characters = getCharacters;
          console.log(this.characters)  
          
        } catch (error) {
          console.log(error);
          throw error;          
        }





      } else {
        this.page = 1;
      }

    }

  },  
  created(){
    this.obtenerPersonajes();   
   

    		


  }


  
}

</script>


<style >
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;800&display=swap');

body {
  background-color: #24282F  !important;
}

h1 {
  font-family: 'Inter', sans-serif;
  font-weight: 800;
  font-size: 5.325rem !important;
  color:#5dff18; 
}
.card {
  background-color: #3C3E44 !important;
}

.btn {
  margin-left: 5px;

  
}

.isAlive{
  background: #55CC44;
  width: 20%;
  border-radius: 7%;
  text-align: center;
  color:#3C3E44;  
}

.isDead{
  background: #EF4444;
  width: 30%;
  border-radius: 7%;
  text-align: center;
  color:#f8f9fa; 
  padding-right: 5px;
  padding-left: 5px;
}
.isUnknown{
  
  background: #ffc107;
  width: 40%;
  border-radius: 7%;
  text-align: center;
 color:#3C3E44; 
}


span {
  font-size: 14px;

}
button:hover {
  background-color: #55CC44 !important;
  /* border: 1px solid grey; */
}


 


</style>
