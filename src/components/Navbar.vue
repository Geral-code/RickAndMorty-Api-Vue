<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
  <div class="container-fluid">
    <router-link class="navbar-brand" to ="/">Rick and Morty</router-link>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav">
        <li class="nav-item">
          <router-link class="nav-link"  to ="/">Home</router-link>
        </li>
        <li class="nav-item">
          <router-link class="nav-link" to="/Characters">Characters</router-link>
        </li>
       </ul>
    </div>
  </div>
</nav>
</template>

<script>
export default {

}
</script>

<style scoped>
.navbar {
  background-color: #6c757d !important;
}
.navbar-brand {
  font-family: "Inter", sans-serif;
  color: #dde2da !important;
}

.nav-link {
  
  color: #ebebe5 !important;
  border-radius: 5%;
  border-color: black;
}
.nav-link:hover {
  
  background-color:#585b61 ;
  color: #5dff18 !important;
  border-radius: 5%;
  border-color: black;
}


</style>