<template>
    <div class="viewContainer centerContainer-v">
        <NavBar class="navBar"></NavBar>
    </div>
</template>

<script setup>
import NavBar from '../menuBar/NavBar.vue';
</script>

<style scoped>
.viewContainer{
width: 100%;
height: 100%;
margin: 0px;
padding: 0px;
/* border: solid blue 1px; */
}
.navBar{
    width: 50%;
    position: fixed;
    /* border: solid red 1px; */
}


</style>