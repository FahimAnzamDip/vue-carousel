<script setup>
import images from "./data/images.js";
import { ref } from "vue";

let currentSlide = ref(0);
</script>

<template>
    <div class="container px-5 mx-auto h-screen flex justify-center items-center">
        <div class="max-w-4xl">
            <!-- Slide -->
            <div class="relative">
                <img class="rounded-xl w-100 h-auto aspect-[3/2] shadow-xl" :src="images[currentSlide].url" :alt="images[currentSlide].caption" />
                <ul class="flex text-white text-xl space-x-5 absolute bottom-[20px] left-[50%] -translate-x-[50%] backdrop-blur-sm px-4 py-1 rounded-xl">
                    <li @click.prevent="currentSlide = index" v-for="(image, index) in images" :key="index" :class="index === currentSlide ? 'scale-120 text-white' : 'scale-75 text-white/70'" class="font-bold text-base md:text-lg cursor-pointer">{{ index + 1 }}</li>
                </ul>
            </div>

            <!-- Control Buttons -->
            <div class="flex justify-center mt-8 space-x-7">
                <!-- Previous Button -->
                <button @click.prevent="currentSlide > 0 ? currentSlide-- : (currentSlide = images.length - 1)" type="button" class="bg-orange-600 rounded-xl flex justify-center items-center py-2 px-5 space-x-1 hover:scale-125 transition-all duration-300 text-white">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5 md:w-6 md:h-6">
                        <path fill-rule="evenodd" d="M15.79 14.77a.75.75 0 01-1.06.02l-4.5-4.25a.75.75 0 010-1.08l4.5-4.25a.75.75 0 111.04 1.08L11.832 10l3.938 3.71a.75.75 0 01.02 1.06zm-6 0a.75.75 0 01-1.06.02l-4.5-4.25a.75.75 0 010-1.08l4.5-4.25a.75.75 0 111.04 1.08L5.832 10l3.938 3.71a.75.75 0 01.02 1.06z" clip-rule="evenodd" />
                    </svg>
                    <span class="font-medium text-sm md:text-base">Prev</span>
                </button>
                <!-- Next Button -->
                <button @click.prevent="currentSlide < images.length - 1 ? currentSlide++ : (currentSlide = 0)" type="button" class="bg-orange-600 rounded-xl flex justify-center items-center py-2 px-5 space-x-1 hover:scale-125 transition duration-300 text-white">
                    <span class="font-medium text-sm md:text-base">Next</span>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20" fill="currentColor" class="w-5 h-5 md:w-6 md:h-6">
                        <path fill-rule="evenodd" d="M10.21 14.77a.75.75 0 01.02-1.06L14.168 10 10.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z" clip-rule="evenodd" />
                        <path fill-rule="evenodd" d="M4.21 14.77a.75.75 0 01.02-1.06L8.168 10 4.23 6.29a.75.75 0 111.04-1.08l4.5 4.25a.75.75 0 010 1.08l-4.5 4.25a.75.75 0 01-1.06-.02z" clip-rule="evenodd" />
                    </svg>
                </button>
            </div>
        </div>
    </div>
</template>

<style scoped>

</style>
