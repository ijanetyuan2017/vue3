<template>
   <Header></Header>
   <div class="content">
    <div class="content-left"> <Menu></Menu></div>
    <div class="content-right"><RouterView /></div>
   </div>

</template>

<script setup>
import Header from '../components/Header.vue'
import Menu  from  '../components/Menu.vue'
// import {Menu} from '../components/menu/Menu.vue'
 import {RouterView } from 'vue-router'

</script>
<style scoped>

.content{
    width:100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    align-items: center;
}
</style>


