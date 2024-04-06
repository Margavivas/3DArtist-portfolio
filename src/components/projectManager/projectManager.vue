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
        <section class="right"></section>
    </div>
</template>

<script setup>
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
    margin-top: 35%;
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
    /* border: solid 1px blue; */
}
</style>