<template>
  <div
    @mouseover="showDir = false"
    @mouseleave="showDir = true"
    class="fixed cursor-pointer rounded-full h-5 w-5 z-10 shadow-[0px_0px_2px_2px_rgba(0,0,0,0.5)]"
    :class="[animateDot(), dotStyle]"
  >
    <div
      v-if="showDir"
      class="rounded-full h-3 w-3 top-4 border"
      :class="[eyeballStyle, eyeballBorderStyle]"
    ></div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import Marker from "./Marker.vue";
const showDir = ref(true);
const eyeballStyle = ref();
const eyeballBorderStyle = ref();
const dotStyle = ref();

function animateDot() {
  return "hover:rounded-l-lg hover:bg-zinc-200 hover:rounded-md hover:h-20 hover:z-[1000] hover:w-[300px] hover:!shadow-[0px_0px_2px_3px_rgba(0,0,0,0.15)] transition-all duration-70";
}

function randomColorize() {
  const months = ["bg-red-500", "bg-green-500", "bg-black"];

  const random = Math.floor(Math.random() * months.length);
  eyeballStyle.value = months[random];
  if (months[random] === "bg-black") {
    dotStyle.value = "bg-zinc-800";
    eyeballBorderStyle.value = "border border-black";
  } else if (months[random] === "bg-red-500") {
    dotStyle.value =
      "bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500";
    eyeballBorderStyle.value = "border border-yellow-500";
  } else {
    dotStyle.value =
      "bg-gradient-to-r from-indigo-500 from-10% via-sky-500 via-30% to-emerald-500 to-90% hover:bg-indigo-500";
    eyeballBorderStyle.value = "border border-orange-500";
  }
}
function getRandomArbitrary(min, max) {
  return Math.random() * (max - min) + min;
}
randomColorize();
</script>
