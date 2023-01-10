<script setup>
import {RouterLink, RouterView} from 'vue-router'
</script>

<template>

  <nav>
    <RouterLink to="/">Home</RouterLink> &nbsp;
    <RouterLink to="/about">About</RouterLink>
  </nav>
  <hr>

  <RouterView/>
</template>

<style scoped>

</style>
