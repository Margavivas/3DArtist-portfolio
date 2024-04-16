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
#viewContainer {
    width: 100%;
    height: 100%;
    margin: 0px;
    padding: 0px;
    position: relative;
    box-shadow: inset 0 0 0 15px var(--border-color); 
    border-radius: 30px;
    background-color: var(--back-standard-color);
    transition: all 0.8s ease-in-out; 
}

.navBar {
    position: fixed;
}

.bar-v {
    position: fixed;
    left: -1px;
    top: 65vh;
}

.bar-right {
    left: 100vw;
    margin-left: 1px;
    top: 4%;
    transform: scaleX(-1);
    transform-origin: left;
}

.bar-h {
    position: fixed;
    bottom: 0px;
    left: 22vw;
}
</style>
