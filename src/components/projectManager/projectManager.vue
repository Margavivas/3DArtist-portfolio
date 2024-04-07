<template>
    <div class="projectManagerContainer">
        <section class="left">
            <section class="infoContainer">
                <h2>Organic Modeling</h2>
                <h1>Building</h1>
                <p class="paragraph">Algun texto descriptivo introductorio del proyecto</p>
            </section>
            <section class="prev-model">
                <h3>Previous Model</h3>
                <div class="prev-container-img card">
                    <img src="./img/image-test.png" alt="prev-image">
                </div>
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
        <section class="center"></section>
        <section class="right">
        <video class="borderContainer" 
            @mouseenter="HandleOverVideo" 
            @mouseleave="ExitOverVideo" 
            @touchstart="HandleOverVideo"
            src="./videos/video-1.mp4" 
            :controls="isHoverVideo">
        </video>
        <section class="programs">
            <h3>Programs Used</h3>
            <section class="programsContainer">
                <p class="program bold">Zbrush</p>
                <p class="program bold">holi</p>
            </section>
        </section>
        <section class="next-model">
                <h3>Next Model</h3>
                <div class="next-container-img card">
                    <img src="./img/image-test.png" alt="prev-image">
                    <section>
                        <h4>model name</h4>
                        <p class="next-model-description">Personaje creado creado cedjdhj djkqieuwomnd,n d</p>
                    </section>
                </div>
            </section>
        </section>
    </div>
</template>

<script setup>
import {ref} from 'vue';
let isHoverVideo = ref(false);

function HandleOverVideo () {
        isHoverVideo.value = true; 
}
function ExitOverVideo () {
    isHoverVideo.value = false; 
}
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
    justify-content: space-around;
    /* border: solid 1px blue;    */
}
.paragraph{
    margin-top: 20px;
    color: var(--text-color);
} 
.infoContainer{
    margin-top: 150px;
    width: 70%;
    height: fit-content;
    /* border: solid 1px red; */
}

h3{
    color: var(--white-color);
}
.prev-model{
    margin-top: 20%;
    width: 70%;
    height: 180px;
    /* border: solid 1px red; */
    display: flex;
    flex-direction: column;
    justify-content: space-around;
}
.socialMediaContainer{
    width: 70%;
    /* border:solid red 1px; */
}


.center{
    width: 35%;
    height: 100%;
    /* border: solid 1px blue; */
}
.right{
    width: 32%;
    height: 100%;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: space-around;
    /* border: solid 1px blue; */
}
video{
    margin-top: 100px;
    transition: all 0.5s ease-in-out;
}

.next-model, .programs, video{
    width: 70%;
}

.next-container-img{
    display: flex;
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


</style>