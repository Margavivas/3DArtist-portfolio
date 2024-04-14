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
                <!-- <TresCanvas
                shadows
                alpha
                >
                <TresPerspectiveCamera
                    :position="[0, 0, 4.5]" 
                    :look-at="[0, 0, 0]"
                />
                    <OrbitControls />
                    <Suspense>
                    <FBXModel
                    path="http://localhost:5173/src/components/projectManager/3dModels/AvelynFinal.fbx"
                    :position="[0, -1.8, 0]"
                    :scale="0.02"
                    />
                    </Suspense>
                    <TresDirectionalLight
                    :intensity="2"
                    :position="[3, 3, 3]"
                    />
                    <TresAmbientLight />
                </TresCanvas> -->
                <slider></slider>
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
                <p class="program bold"
                v-for="(program, key) in currentProject.programs"
                :key="key"
                >{{program}}</p>
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
        </section>
        <Transition>
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
import {ref, onMounted, watch} from 'vue';
import { TresCanvas} from '@tresjs/core';
import { OrbitControls, FBXModel } from '@tresjs/cientos';
import slider from './components/slider/slider.vue';

//import data
import projectDataInfo from './assets/projects3d.json'

//variables
let isHoverVideo = ref(false);
let projectData = ref([]);
let currentProject = ref([]);
let imageOpen = ref('');
let isImageOpen = ref(false);



//functions
function GetProjectsData (){
    projectData.value = projectDataInfo.proyectos3D;
    console.log('project data was loaded successfully ', projectData.value);
}

function GetCurrentProject (project){
    currentProject.value = projectData.value[project];
    console.log('saving current project ', currentProject.value);
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


// watch(modelPath, (newPath, oldPath) => {
//     console.log('La ruta del modelo 3D ha cambiado:', newPath , '   ', oldPath);
// });



onMounted(() => {
    GetProjectsData();
    GetCurrentProject('AvelynFinal'); 
});

   

</script>

<style scoped>
.projectManagerContainer{
    width: 100vw;
    height: 100vh;
    display: flex;
    justify-content: space-around;
    /* border: solid red 1px; */
    /* padding: 20px; */
}
.left{
    width: 32%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 10%;
    /* justify-content: space-around; */
    position: relative;
    /* border: solid 1px blue;    */
}
.paragraph{
    margin-top: 20px;
    color: var(--text-color);
} 
.infoContainer{
    margin-top: 170px;
    width: 70%;
    max-width: 70%;
    height: fit-content;
    /* border: solid 1px red; */
}

.modelIU{
    width: 70%;
    height: max-content;
    display: flex;
    gap: 10px;
}

.imagesContainer{
    max-width: 100%;
    width: fit-content;
    height: max-content;
    display: flex;
    gap: 10px;
    overflow: hidden;
    overflow-x: scroll;
}

h3{
    color: var(--white-color);
}
.prev-model{
    /* margin-top: 20%; */
    width: 70%;
    height: 180px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    position: absolute;
    bottom: 40px;
}
.socialMediaContainer{
    height: max-content;
    width: 70%;
    /* border:solid red 1px; */
}


.center{
    width: 35%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-evenly;
    /* border: solid 1px blue; */
}
.modelContainer{
    width: 100%;
    height: 80%;
    /* border: solid red 1px; */
    cursor: grab;
    /* margin-top: 40px; */
}
.right{
    width: 32%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    /* justify-content: space-around; */
    gap: 10%;
    /* border: solid 1px blue; */
    position: relative;

}
video{
    margin-top: 150px;
    transition: all 0.5s ease-in-out;
}

.next-model, .programs, video{
    width: 70%;
}

.next-model{
    position: absolute;
    bottom: 40px;
}
.next-container-img{
    display: flex;
    float: right;
    gap: 5%;
}
.next-model>h3, .programs>h3{
    margin-bottom: 10px;
    text-align: right;
}
.next-model-description{
    margin-top: 5px;
}

.programs>h3{
    color: var(--black-color);
}
.programsContainer{
    display: flex;
    justify-content: flex-end;
    gap: 10px;
}

.image{
    cursor: pointer;
    border-radius: 10px;
    max-width: 150px;
    max-height: 150px;
}

.imageContainer{
    width: fit-content;
    height: fit-content;
    position: relative;
}
.imageFullSize{
    width: fit-content;
    height: fit-content;
    max-width: 800px;
}

.close{
    width: 30px;
    height: 30px;
    border-radius: 100%;
    background-color: var(--white-color); 
    position: absolute;
    right: -15px;
    top: -15px;
    cursor: pointer;
    transition: all 0.3s ease-in-out;
}
.close:hover{
    background-color: var(--black-color); 
    color: var(--white-color);
}
.v-enter-active,.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,.v-leave-to {
  opacity: 0;
}


</style>