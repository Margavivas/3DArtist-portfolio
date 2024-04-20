<template>
    <div class="projectManagerContainer">
        <section class="left">
            <section class="infoContainer">
                <h2>{{ currentProject.subtitle }}</h2>
                <h1>{{ currentProject.projectName }}</h1>
                <p class="paragraph">{{ currentProject.text }}</p>
            </section>
            <section class="modelIU">
                <div class="imagesContainer card">
                    <img 
                    class="image"
                    v-for="(image, key) in currentProject.images"
                    :key="key"
                    :src="getURL(image)"
                    :alt="`./img/${currentProject.projectName}/image-test.png`"
                    @click="openImage(image)"
                    >
                </div>
            </section>
            <section class="prev-model">
                <h3>Previous Model</h3>
                <div class="prev-container-img card">
                    <img src="./img/image-test.png" alt="prev-image">
                </div>
            </section>
        </section>
        <section class="center">
            <section class="modelContainer">
                <slider
                @currentModel = "HandleCurrentModel"
                @nextModel = "HandleNextModel"
                @previousModel = "HandlePrevioustModel"
                ></slider>
            </section>
            <section class="socialMediaContainer">
                <ul class="social-list">
                    <li class="socialMedia centerContainer-v centerContainer-h"><img  src="./img/social-media/instagram.svg" alt="instagram"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/artstation.svg" alt="art-station"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/tik-tok.svg" alt="tiktok"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/linkedin.svg" alt="linkedin"></li>
                </ul>
            </section> 
        </section>
        <section class="right">
        <video class="borderContainer" 
            @mouseenter="HandleOverVideo" 
            @mouseleave="ExitOverVideo" 
            @touchstart="HandleOverVideo"
            :src="getURL(currentProject.video)" 
            :controls="isHoverVideo">
        </video>
        <section class="programs">
            <h3>Programs Used</h3>
            
            <section class="programsContainer">
             <transition-group name="programs" tag="p" class="programsContainer">
                <p class="program bold"
                v-for="(program, key) in currentProject.programs"
                :key="key"
                >{{program}}</p>
            </transition-group>
            </section>
        </section>
        <section class="next-model">
                <h3>Next Model</h3>
                <div class="next-container-img card">
                    <img src="./img/image-test.png" alt="prev-image">
                    <!-- <section>
                        <h4>model name</h4>
                        <p class="next-model-description">Personaje creado creado cedjdhj djkqieuwomnd,n d</p>
                    </section> -->
                </div>
            </section>
            <section class="socialMediaContainer-phone">
                <ul class="social-list">
                    <li class="socialMedia centerContainer-v centerContainer-h"><img  src="./img/social-media/instagram.svg" alt="instagram"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/artstation.svg" alt="art-station"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/tik-tok.svg" alt="tiktok"></li>
                    <li class="socialMedia centerContainer-v centerContainer-h"><img src="./img/social-media/linkedin.svg" alt="linkedin"></li>
                </ul>
            </section> 
        </section>
        <section class="rotation-element">
            <img src="./rotate-animations/rotate-animation.gif" alt="rotate animation icon">
        </section>
        <Transition name="fade">
            <section class="showFullImage" v-if="isImageOpen">
                <div class="imageContainer">
                    <div class="close centerContainer-v centerContainer-h bold" 
                    @click="isImageOpen = false">x</div>
                    <img 
                    :src="getURL(imageOpen)" 
                    :alt="`${currentProject.projectName} image`"
                    class="imageFullSize borderContainer"
                    >
                </div>
            </section>
        </Transition>
    </div>
</template>

<script setup>
import {ref, onMounted, getCurrentInstance} from 'vue';
import slider from './components/slider/slider.vue';

//import data
import projectDataInfo from './assets/projects3d.json'

//variables
let isHoverVideo = ref(false);
let projectData = ref([]);
let currentProject = ref([]);
let imageOpen = ref('');
let isImageOpen = ref(false);
let { emit } = getCurrentInstance();



//functions
function GetProjectsData (){
    projectData.value = projectDataInfo.proyectos3D;
    console.log('project data was loaded successfully ', projectData.value);
}

function GetCurrentProject (project){
    currentProject.value = projectData.value[project];
    console.log('saving current project ', currentProject.value);
    emit('currentColor', currentProject.value.bgColor);
    console.log('current color - ', currentProject.value.bgColor);
}

function HandleOverVideo () {
        isHoverVideo.value = true; 
}
function ExitOverVideo () {
    isHoverVideo.value = false; 
}

function getURL(element){
return new URL(element, import.meta.url).href
}

function openImage(image){
    isImageOpen.value = true;
    // console.log('open image ', image);
    imageOpen.value = image;
}

function HandleCurrentModel(message){
    console.log('child message :', message);
    GetCurrentProject(message); 
}

function HandleNextModel(message){
    console.log('child next message :', message);
}

function HandlePrevioustModel(message){
    console.log('child previous message :', message);
}


onMounted(() => {
    GetProjectsData();
    GetCurrentProject('AvelynFinal'); 
});

   

</script>

<style scoped>
@import './style/projectManager.css';
@import './style/responsive-projectManager.css';
</style>