<template>
  <div
    ref="preloader"
    class="preloader z-50 fixed top-0 min-h-full min-w-full backdrop-blur-sm bg-white/50 flex flex-col justify-center w-full items-center"
  >
    <Preloader />
    <div class="text-center">
      <div ref="counter" class="counter text-5xl mt-4 bebas text-zinc-800">
        1
      </div>
      <div class="flex flex-row">
        <div ref="loadedMsg">Vehicles loaded</div>
      </div>
    </div>
  </div>
  <img class="!min-h-screen !min-w-[2500px]" src="../assets/map-cagliari.png" />
</template>
<script setup>
import { ref, onMounted } from "vue";
import { useTimeoutFn } from "@vueuse/core";
import { gsap } from "gsap";
import Preloader from "@/components/Preloader.vue";

const preloader = ref(null);
const counter = ref(null);
const tl = gsap.timeline({ paused: false });
const tl2 = gsap.timeline({ paused: false });
const startcount = 1;
const end = 87;
const loadedMsg = ref();

const emit = defineEmits(["preloaded"]);

function fadeOut() {
  tl.add("blueGreenSpin", "+=.75");
  tl.to(
    ".preloader",
    {
      duration: 0.25,
      autoAlpha: 0,
      y: "+=50",
      ease: "back.in(1.7)",
      onComplete: () => {
        emit("preloaded");
      },
    },
    "blueGreenSpin"
  );
}

onMounted(() => {
  tl2.fromTo(
    ".counter",
    {
      innerText: startcount,
      scale: 0.8,
    },
    {
      innerText: end,
      snap: { innerText: 1 },
      duration: 2,
      ease: "linear",
      onUpdate: () => {
        counter.innerText = counter.innerText;
      },
      onComplete: () => {
        fadeOut();
      },
    }
  );
});
</script>
