<template>
    <div class="centerContainer-v" id="viewContainer" :style="{ backgroundColor }">
        <NavBar class="navBar"></NavBar>
        <img src="./img/bar-v.svg" alt="bar-vertical-left" class="bar-v">
        <img src="./img/bar-v.svg" alt="bar-vertical-right" class="bar-v bar-right">
        <img src="./img/bar-h.svg" alt="bar-horizontal" class="bar-h">
        <projectManager
        @currentColor="HandleBackgroundColor"
        ></projectManager>
    </div>
</template>

<script setup>
import { ref } from 'vue';
import NavBar from '../menuBar/NavBar.vue';
import projectManager from '../projectManager/projectManager.vue';

//variables
let backgroundColor = ref('');

//functions
function HandleBackgroundColor(message){
    console.log('background color - ', message);
    backgroundColor.value = message;
}
</script>

<style scoped>
@import './style/viewContainer.css'
</style>
