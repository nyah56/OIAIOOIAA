<template>


    <div class="flex-col flex justify-center items-center">
        <h3>{{ dayName(date, 'id') }}</h3>
        <h4>{{ dateNow }}</h4>
        <img src="/cat.png" class="w-48 h-48 rounded-full object-cover animate-car" alt="OIAOO" srcset=""
            v-if="toggleActive">
        <div v-else>
            <video src="/cat.webm" class="w-48 h-48 rounded-full object-cover" autoplay loop muted preload></video>
        </div>
        <audio :src="srcSound" ref="carSound" preload="auto" @ended="loopCarSound"></audio>
        <div>
            <button class="bg-blue-500 text-white py-2 px-4 rounded-md cursor-pointer mt-8 hover:bg-cyan-500"
                @pointerdown="toggleActive = false" @pointerup="toggleActive = true"
                @pointerleave="toggleActive = true">
                <IconPlay v-if="toggleActive" />
                <IconPause v-else />
            </button>
        </div>
    </div>

</template>
<script setup>
import { ref, onUpdated, onMounted } from 'vue';
import IconPlay from "./icons/IconPlay.vue";
import IconPause from "./icons/IconPause.vue";

let date = new Date();
const dateNow = date.toLocaleDateString("id");
const dayName = (date, locale) => date.toLocaleDateString(locale, { weekday: 'long' });
const carSound = ref(null);
const srcSound = ref('oiiai.mp3');
// const hours = 6
// const isDayTime = hours > 5 && hours < 17;
// if(isDayTime === true){
//   document.write('day');
// } else {
//     document.write('night');

// }

let toggleActive = ref(true);
const START_TIME_SOUND = 0.19;
// let carSound = new Audio('oiiai.mp3');
const loopCarSound = () => {
    if (!toggleActive.value) {
        carSound.value.currentTime = START_TIME_SOUND;
        let carPromise = carSound.value.play();

        if (carPromise !== undefined) {
            carPromise.then(_ => {
                // Automatic playback started!
                // Show playing UI.
                // carSound.value.load();
                // carSound.value.currentTime = START_TIME_SOUND;
                // carSound.value.play()
                // carSound.value.pause()
                // console.log(carPromise);
            })
                .catch(error => {
                    // Auto-play was prevented
                    // Show paused UI.
                    console.error(error)
                    // carSound.value.pause()
                });
        }

    }



}

onMounted(() => {

});
onUpdated(() => {
    //   console.log(!toggleActive.value?carSound.value.src:'');

    carSpinSound();
})
const carSpinSound = () => {
    !toggleActive.value ? loopCarSound() : carSound.value.pause();
    carSound.value.currentTime = START_TIME_SOUND;
}


</script>