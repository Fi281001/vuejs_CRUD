<script setup>
import { RouterLink, RouterView } from 'vue-router'

</script>

<template>


      <nav> 
        <RouterLink to="/about">add</RouterLink>
        <hr/>
        
        <RouterLink to="/">Home</RouterLink>
      </nav>      


  <RouterView />
</template>

<style >
  
</style>
