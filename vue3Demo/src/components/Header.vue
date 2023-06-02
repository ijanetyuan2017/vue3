<template>
    <div class="header">{{userName}}welcome this is my header</div>
</template>
<script setup>
import {ref} from 'vue'
const userName=ref('');
</script>
<style scoped>
.header{
    width:100%;
    height: 50px;
    color: gray;
    display: flex;
    flex-direction: row;
    justify-content: center;
    align-items: center;
}
</style>
