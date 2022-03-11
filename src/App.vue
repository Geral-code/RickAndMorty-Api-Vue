<template>
<Navbar/>
<Modal/>

  <router-view/>
</template>

<script>
import Navbar from '@/components/Navbar.vue';
import Modal from '@/components/Modal.vue';

export default {
  components: {
    Navbar,
    Modal
  
    
    
  },
}
</script>




<style>

</style>
