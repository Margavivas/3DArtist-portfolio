<template>
  <div class="slidercontainer">
    <section class="model">
      <TresCanvas shadows alpha v-if="currentModel === 'AvelynFinal'">
        <TresPerspectiveCamera :position="[0, 0, 4.5]" :look-at="[0, 0, 0]" />
        <OrbitControls />
        <Suspense>
          <FBXModel
            path="http://localhost:5173/src/components/projectManager/3dModels/AvelynFinal.fbx"
            :position="[0, -1.8, 0]"
            :scale="0.02"
          />
        </Suspense>
        <TresDirectionalLight :intensity="2" :position="[3, 3, 3]" />
        <TresAmbientLight />
      </TresCanvas>

      <TresCanvas shadows alpha v-if="currentModel === 'proyecto2'">
        <TresPerspectiveCamera :position="[11, 11, 11]" />
        <OrbitControls />
        <Suspense>
          <FBXModel
            path="https://raw.githubusercontent.com/Tresjs/assets/main/models/fbx/low-poly-truck/Jeep_done.fbx"
            :scale="0.015"
          />
        </Suspense>
        <TresDirectionalLight :intensity="2" :position="[3, 3, 3]" />
        <TresAmbientLight />
      </TresCanvas>

      <TresCanvas shadows alpha v-if="currentModel === 'proyecto3'">
        <TresPerspectiveCamera :position="[11, 11, 11]" />
        <OrbitControls />
        <Suspense>
          <FBXModel
            path="http://localhost:5173/src/components/projectManager/3dModels/AvelynFinal.fbx"
            :scale="0.015"
          />
        </Suspense>
        <TresDirectionalLight :intensity="2" :position="[3, 3, 3]" />
        <TresAmbientLight />
      </TresCanvas>
    </section>
    <section class="sliderArrows">
        <div class="left centerContainer-h centerContainer-v" @click="HandleLeftButton">
            <h4><</h4>
        </div>
        <div class="right centerContainer-h centerContainer-v" @click="HandleRightButton"><h4>></h4></div>
    </section>
  </div>
</template>

<script setup>
import { ref, onMounted, watch, getCurrentInstance } from "vue";
import { TresCanvas } from "@tresjs/core";
import { OrbitControls, FBXModel } from "@tresjs/cientos";

//vars
const models = ["AvelynFinal", "proyecto2", "proyecto3"];
let currentModel = ref("");
let currentIndex = ref(0);
let { emit } = getCurrentInstance();


//functions
function HandleRightButton(){
    console.log('click right');
    if(currentIndex.value < (models.length - 1)){
        currentIndex.value ++;
        console.log('condicion right');
    }else{
        currentIndex.value = 0; 
    }
    // if(models[currentIndex.value+1] == undefined){
    //   emit('nextModel',  models[0]);
    // }else{
    //   emit('nextModel',  models[currentIndex.value+1]);
    // }
    
}

function HandleLeftButton(){
    console.log('click left');
    if(currentIndex.value > 0){
        currentIndex.value --;
        console.log('condicion left');   
    }else{
        currentIndex.value = models.length - 1;
    }
}


watch(currentIndex, (newIndex, oldIndex) => {
    console.log('index change:', 'new value - ', newIndex , '  old - ', oldIndex);
    currentModel.value = models[newIndex];
     console.log('model change:', currentModel.value);

     if(oldIndex){ // send previous model
        currentModel.value = undefined;
        console.log('test - ', currentModel.value);
        setTimeout(() => {
            currentModel.value = models[newIndex];
            console.log('test - 2 -', currentModel.value);
            emit('currentModel', currentModel.value);
        }, 1);
     }else{
        emit('currentModel', currentModel.value);
     }
     emit('previousModel', models[oldIndex]);

     if(newIndex < (models.length - 1)){ // send next model
      emit('nextModel',  models[newIndex + 1]);
     }else{
      emit('nextModel',  models[0]);
     }
    
});

onMounted(() => {
  currentModel.value = models[currentIndex.value];
  console.log("current Model in click left view - ", currentModel.value);
  console.log(models.length);
});
</script>

<style scoped>
.slidercontainer{
  width: 100%;
  height: 100%;
  /* border: solid red 1px; */
  position: relative;
  z-index: 1;
}
.model{
  width: 100%;
  height: 100%;
}
.sliderArrows{
    width: 120%;
    /* border: solid red 1px; */
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: absolute;
    left: -10%;
    top: 80%;
    z-index: 2;
}

.right, .left{
    min-width: 50px;
    min-height: 50px;
    border-radius: 100%;
    background-color: var(--white-color);
    transition: all 0.3s ease-in-out;
    cursor: pointer;
}
.right:hover, .left:hover{
    background-color: var(--black-color);
    color:var(--white-color);
}
</style>
