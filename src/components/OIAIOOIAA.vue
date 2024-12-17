
<template>


    <div
        class="flex-col flex justify-center items-center">
        <img src="/cat.png" class="w-48 h-48 rounded-full object-cover animate-car" alt="OIAOO" srcset=""
            v-if="toggleActive">
        <video src="/cat.webm" class="w-48 h-48 rounded-full object-cover" autoplay loop muted v-else preload></video>
    <div>
        <button class="bg-blue-500 text-white py-2 px-4 rounded-md cursor-pointer mt-8 hover:bg-cyan-500"
            @pointerdown="toggleActive = false" @pointerup="toggleActive = true" @pointerleave="toggleActive = true">
           <IconPlay v-if="toggleActive"/>
           <IconPause v-else/>
        </button>
    
       </div>
    </div>
    
</template>
<script setup>
import { ref ,onUpdated } from 'vue';
import IconPlay from "./icons/IconPlay.vue";
import IconPause from "./icons/IconPause.vue";

let toggleActive = ref(true);
const START_TIME_SOUND = 0.19;
let carSound = new Audio('oiiai.mp3');
const loopCarSound = () =>{
    carSound.preload = true;
    carSound.currentTime = START_TIME_SOUND;
    carSound.play();
    carSound.loop = true;
    // console.log(carSound.length)
}
const resetCarSound = ()=>{
    carSound.pause();
    carSound.currentTime = START_TIME_SOUND;
}

onUpdated(() => {
  
  carSpinSound();
})
const carSpinSound = () =>{
    !toggleActive.value?loopCarSound():resetCarSound();
}


</script>