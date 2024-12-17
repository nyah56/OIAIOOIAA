<script setup>
</script>

<template>

    <div
        class="flex-col flex justify-center items-center rounded-lg bg-white p-6 text-surface shadow-secondary-1 dark:bg-surface-dark dark:text-white">


        <img src="/cat.png" class="w-48 h-48 rounded-full object-cover animate-car" alt="OIAOO" srcset=""
            v-if="toggleActive">
        <video src="/cat.webm" class="w-48 h-48 rounded-full object-cover" autoplay loop muted v-else></video>
        <!-- <audio src="../assets/oiiai.mp3" autoplay loop v-else></audio> -->
        <button class="bg-blue-500 text-white py-2 px-4 rounded-md cursor-pointer mt-8 hover:bg-cyan-500"
            @click="carSpin">
            <svg width="20" height="20" viewBox="0 0 25 24" fill="#343C54" xmlns="http://www.w3.org/2000/svg"
                transform="rotate(0 0 0)" v-if="toggleActive">
                <path fill-rule="evenodd" clip-rule="evenodd"
                    d="M19.4357 13.9174C20.8659 13.0392 20.8659 10.9608 19.4357 10.0826L9.55234 4.01389C8.05317 3.09335 6.125 4.17205 6.125 5.93128L6.125 18.0688C6.125 19.828 8.05317 20.9067 9.55234 19.9861L19.4357 13.9174ZM18.6508 11.3609C19.1276 11.6536 19.1276 12.3464 18.6508 12.6391L8.76745 18.7079C8.26772 19.0147 7.625 18.6552 7.625 18.0688L7.625 5.93128C7.625 5.34487 8.26772 4.9853 8.76745 5.29215L18.6508 11.3609Z"
                    fill="#d2d2d2" />
            </svg>
            <svg width="20" height="20" viewBox="0 0 25 24" fill="#d2d2d2" xmlns="http://www.w3.org/2000/svg"
                transform="rotate(0 0 0)" v-else>
                <path fill-rule="evenodd" clip-rule="evenodd"
                    d="M7 3.25C5.75736 3.25 4.75 4.25736 4.75 5.5V18.4999C4.75 19.7426 5.75736 20.75 7 20.75H8.75C9.99264 20.75 11 19.7426 11 18.4999V5.5C11 4.25736 9.99264 3.25 8.75 3.25H7ZM6.25 5.5C6.25 5.08579 6.58579 4.75 7 4.75H8.75C9.16421 4.75 9.5 5.08579 9.5 5.5V18.4999C9.5 18.9142 9.16421 19.2499 8.75 19.2499H7C6.58579 19.2499 6.25 18.9142 6.25 18.4999V5.5Z"
                    fill="#d2d2d2" />
                <path fill-rule="evenodd" clip-rule="evenodd"
                    d="M16.25 3.25C15.0074 3.25 14 4.25736 14 5.5V18.4999C14 19.7426 15.0074 20.75 16.25 20.75H18C19.2426 20.75 20.25 19.7426 20.25 18.4999V5.5C20.25 4.25736 19.2426 3.25 18 3.25H16.25ZM15.5 5.5C15.5 5.08579 15.8358 4.75 16.25 4.75H18C18.4142 4.75 18.75 5.08579 18.75 5.5V18.4999C18.75 18.9142 18.4142 19.2499 18 19.2499H16.25C15.8358 19.2499 15.5 18.9142 15.5 18.4999V5.5Z"
                    fill="#d2d2d2" />
            </svg>


        </button>
    </div>
    <!-- <div class="bg-linear-45 from-indigo-500 via-purple-500 to-pink-500"></div> -->
</template>
<script setup>
import { ref } from 'vue';


let toggleActive = ref(true);

let mySound = new Audio('oiiai.mp3');
const carSpin = () =>{
    toggleActive.value = !toggleActive.value;
    !toggleActive.value?mySound.play():'';
}


</script>