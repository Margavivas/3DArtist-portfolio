<template>
    <div class="navBarContainer centerContainer-v centerContainer-h borderContainer">
        <ul>
            <li class="bold">About Me</li>
            <li><img src="./img/logo.svg" alt="Manez Logo"></li>
            <li class="bold">Contact</li>
        </ul>
    </div>
</template>

<style scoped>
@import '../../style.css';
.navBarContainer{
    width: 480px;
    height: 60px;
    background-image: url(./img/navBar-bg.svg);
    background-size: contain;
    background-repeat: no-repeat;
    /* border: solid blue 1px; */
}

li{
    cursor: pointer;
}


</style>