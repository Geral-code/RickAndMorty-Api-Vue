<template>
  <!-- <div :class="personaje.status=='Dead'? 'bg-danger' : personaje.status=='unknown' ? 'bg-warning ' : 'bg-success'"> -->

  <div  v-if="personaje.status === 'Alive'" class="is_alive"  >

    <div
      class="
        name
        d-flex
        mb-5
        pt-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <h2>{{ personaje.name }}</h2>
    </div>
    <div
      class="
        container
        d-flex
        mb-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <img class="border border-dark border border-4" :src="personaje.image" alt="" />
    </div>
    <div
      class="
        container-info
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
        
      "
    >
      <!-- <h4>Status: {{ personaje.status }}</h4> -->
    </div>
    <div class="
        container-info
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      ">       
           
 
      <h4>Specie: {{ personaje.species }}</h4>
    </div>
    <div
      class="
        container-info4
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Gender: {{ personaje.gender }}</h4>
    </div>
    <div
      class="
        container-info5
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Origin: {{ personaje.origin.name }}</h4>
    </div>
   
  </div>

   <div v-if="personaje.status === 'Dead'" class="is_dead">
         <div
      class="
        name
        d-flex
        mb-5
        pt-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <h2>{{ personaje.name }}</h2>
    </div>
    <div
      class="
        container
        d-flex
        mb-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <img class="border border-dark border border-4" :src="personaje.image" alt="" />
    </div>
    <div
      class="
        container-info
        d-flex
        mb-1  
        justify-content-center
        animate__animated animate__fadeInUp
        
      "
    >
      <!-- <h4>Status: {{ personaje.status }}</h4> -->
    </div>
    <div class="
        container-info
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      ">       
           
 
      <h4>Specie: {{ personaje.species }}</h4>
    </div>
    <div
      class="
        container-info
        d-flex
        mb-1
        mt-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Gender: {{ personaje.gender }}</h4>
    </div>
    <div
      class="
        container-info5
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Origin: {{ personaje.origin.name }}</h4>
    </div>
   </div>

   <div v-if="personaje.status === 'unknown'" class="is_unknown">

         <div
      class="
        name
        d-flex
        mb-5
        pt-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <h2>{{ personaje.name }}</h2>
    </div>
    <div
      class="
        container
        d-flex
        mb-5
        justify-content-center
        animate__animated animate__fadeInDown
      "
    >
      <img class="border border-dark border border-4" :src="personaje.image" alt="" />
    </div>
    <div
      class="
        container-info
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
        
      "
    >
      
    </div>
    <div class="
        container-info
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      ">       
           
 
      <h4>Specie: {{ personaje.species }}</h4>
    </div>
    <div
      class="
        container-info4
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Gender: {{ personaje.gender }}</h4>
    </div>
    <div
      class="
        container-info5
        d-flex
        mb-1
        justify-content-center
        animate__animated animate__fadeInUp
      "
    >
      <h4>Origin: {{ personaje.origin.name }}</h4>
    </div>
   
  </div>

</template>

<script>
export default {
  data() {
    return {
      personaje: {},
    };
  },

  methods: {
    async obtenerPersonajePorId() {
      try {
        const data = await fetch(
          `https://rickandmortyapi.com/api/character/${this.$route.params.id}`
        );
        const getcharacterid = await data.json();
        this.personaje = getcharacterid;
        console.log(this.personaje);
      } catch (error) {
        console.log(error);
        throw error;
      }
    },
  },
  created() {
    this.obtenerPersonajePorId();
  },
};
</script>

<style scoped>
body {
  background-color: #24282f;
}
h2 {
  font-family: "Inter", sans-serif;
  font-size: 60px;
}
h4 {
  font-family: "Inter", sans-serif;
}
img {
  border-radius: 50%;
  border-image: 10px;
  border-color: black;
  position: relative;
}

.is_alive {
  background-color: #5dff18;
}
.is_dead {
  background-color: #EF4444;
}
.is_unknown {
  background: #ffc107;
}



</style>