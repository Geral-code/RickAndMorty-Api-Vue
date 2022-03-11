<template>
  <h1> {{this.$route.params.id}} </h1>
  <h3> {{ personaje.name}} </h3>
  <img :src="personaje.image" alt="">
  <h4> {{ personaje.status}} </h4>
</template>

<script>
export default {

  data(){
    return {
      personaje: {}
    }
  },

  methods: {

    async obtenerPersonajePorId() {

      try {
        const data = await fetch (`https://rickandmortyapi.com/api/character/${this.$route.params.id}`)
        const getcharacterid = await data.json();
        this.personaje = getcharacterid;
        console.log(this.personaje);
        
      } catch (error) {
        console.log(error);
        throw error;
        
      }
    },

  },
  created () {
    this.obtenerPersonajePorId();

  }


}
</script>

<style>

</style>