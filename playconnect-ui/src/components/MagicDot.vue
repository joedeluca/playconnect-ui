<template>
  <div
    @mouseover="showDir = false"
    @mouseleave="showDir = true"
    class="fixed cursor-pointer rounded-full bg-red-500 h-5 w-5 z-10 shadow-[0px_0px_2px_2px_rgba(0,0,0,0.5)]"
    :class="animateDot()"
  >
    <div v-if="showDir" class="rounded-full bg-blue-500 h-3 w-3"></div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import Marker from "./Marker.vue";
const showDir = ref(true);
function animateDot() {
  return "hover:rounded-l-lg hover:bg-zinc-200 hover:rounded-md hover:h-20 hover:z-[1000] hover:w-[300px] hover:!shadow-[0px_0px_2px_3px_rgba(0,0,0,0.15)] transition-all duration-70";
}
</script>
