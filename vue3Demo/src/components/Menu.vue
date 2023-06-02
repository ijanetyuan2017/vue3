<template>
<ul>
    <li> <RouterLink to="/login">Login</RouterLink></li>
    <li> <RouterLink to="/about">about</RouterLink></li>
    <li> <RouterLink to="/test">test</RouterLink></li>
</ul>
</template>
<script setup>
import { RouterLink } from 'vue-router'
</script>
<style scoped>
nav {
    width:60px;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}
 
</style>
