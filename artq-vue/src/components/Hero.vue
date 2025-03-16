<script setup>
import { ref } from "vue";
import Arrow from "@/components/icons/ArrowDown.vue";

const countdownDate = new Date("March 30, 2025 00:00:00").getTime();

const days = ref(0);
const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

const updateCountdown = () => {
  const now = new Date().getTime();
  const distance = countdownDate - now;

  days.value = Math.floor(distance / (1000 * 60 * 60 * 24));
  hours.value = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60));
  minutes.value = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60));
  seconds.value = Math.floor((distance % (1000 * 60)) / 1000);
};

setInterval(updateCountdown, 1000);
updateCountdown();

const scrollDown = () => {
  window.scroll({
    top: document.body.scrollTop + window.innerHeight,
    behavior: "smooth",
  });
};
</script>

<template>
  <div class="w-full relative h-screen flex flex-col justify-center items-center">
    <div class="uppercase max-w-4xl font-bold flex flex-col justify-center items-center">
      <img src="../assets/img/heroArtq.png" alt="" />
      <!-- <h1 class="md:text-8xl text-6xl">Artqtion</h1>
      <h1 class="md:text-[5.3rem] text-[3.25rem]">Three.Zero</h1> -->
      <h2 class="text-3xl capitalize w-full text-center">Jelajahi masa lalu, ciptakan sejarah baru</h2>
    </div>
    <div class="py-8 px-20 rounded-[3rem] bg-blue-600 gap-y-1 font-semibold gap-x-2 shadow-lg bg-opacity-65 grid grid-cols-3 sm:grid-cols-5 md:grid-cols-7 text-center justify-center items-center my-5">
      <h2 class="text-6xl">{{ days }}</h2>
      <h2 class="text-6xl">:</h2>
      <h2 class="text-6xl">{{ hours }}</h2>
      <h2 class="text-6xl max-sm:hidden">:</h2>
      <h2 class="text-6xl max-sm:hidden">{{ minutes }}</h2>
      <h2 class="text-6xl max-md:hidden">:</h2>
      <h2 class="text-6xl max-md:hidden">{{ seconds }}</h2>
      <h3 class="font-semibold text-lg">Days</h3>
      <span></span>
      <h3 class="font-semibold text-lg">Hours</h3>
      <span class="max-sm:hidden"></span>
      <h3 class="font-semibold text-lg max-sm:hidden">Minutes</h3>
      <span class="max-md:hidden"></span>
      <h3 class="font-semibold text-lg max-md:hidden">Seconds</h3>
      <div class="w-full"></div>
    </div>
    <Arrow class="animate-bounce absolute bottom-0 w-28 -translate-y-20" @click="scrollDown" />
  </div>
</template>
