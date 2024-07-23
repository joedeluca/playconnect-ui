<template>
  <div>
    <div v-if="loaded">
      <template v-for="(dots, index) in totalDots" :key="index">
        <MagicDot :style="randomLocation()" />
      </template>
    </div>
    <FakeMap @preloaded="init" />

    <BaseCard @close="animateSearch" class="search" />
    <div v-if="loaded">
      <SearchBtn
        @click="animateSearch"
        class="fixed top-5 left-5 searchBtn"
        :open="searchOpen"
      />
      <ChartsBtn
        @click="animateBottomDrawer"
        class="fixed bottom-5 left-5 floatingBtn"
        :open="bottomDrawerOpen"
      />
      <SideBarBtn
        @click="animateSideDrawer"
        class="fixed top-5 right-5 sideBarBtn"
        :open="sideDrawerOpen"
      />
      <BottomDrawer
        class="bottomDrawer"
        :class="{ 'opacity-0': bottomDrawerOpen }"
        @close="animateBottomDrawer"
      />
      <SideDrawer
        class="sideDrawer"
        :class="{ 'opacity-0': sideDrawerOpen }"
        @close="animateSideDrawer"
      />
    </div>
  </div>
</template>
<script setup>
import { ref, onMounted } from "vue";
import FakeMap from "@/components/FakeMap.vue";
import BaseCard from "@/components/BaseCard.vue";
import ChartsBtn from "@/components/ChartsBtn.vue";
import BottomDrawer from "@/components/BottomDrawer.vue";
import SideDrawer from "@/components/SideDrawer.vue";
import SideBarBtn from "@/components/SideBarBtn.vue";
import { gsap } from "gsap";
import MagicDot from "@/components/MagicDot.vue";
import SearchBtn from "@/components/SearchBtn.vue";
import Marker from "@/components/Marker.vue";

const loaded = ref(false);
const bottomDrawerOpen = ref(false);
const sideDrawerOpen = ref(false);
const searchOpen = ref(true);
const tl = gsap.timeline({ paused: false });
const totalDots = ref(288);

function init() {
  loaded.value = true;
  animateIntro();
}

onMounted(() => {});

function animateBottomDrawer() {
  if (!bottomDrawerOpen.value) {
    tl.add("finale");
    tl.to(".bottomDrawer", {
      duration: 0.5,
      autoAlpha: 100,
      y: "-=350px",
      ease: "power4.inOut",
    });
    tl.to(
      ".floatingBtn",
      {
        duration: 0.5,
        autoAlpha: 100,
        y: "-=250px",
        ease: "power4.inOut",
      },
      "finale"
    );
    bottomDrawerOpen.value = true;
  } else {
    tl.add("finale");
    tl.to(".bottomDrawer", {
      duration: 0.5,
      autoAlpha: 100,
      y: "+=350px",
      ease: "power4.inOut",
    });
    tl.to(
      ".floatingBtn",
      {
        duration: 0.5,
        autoAlpha: 100,
        y: "+=250px",
        ease: "back.out(1.2)",
      },
      "finale"
    );
    bottomDrawerOpen.value = false;
  }
}

function animateSideDrawer() {
  if (!sideDrawerOpen.value) {
    tl.add("finale");
    tl.to(".sideDrawer", {
      duration: 0.5,
      autoAlpha: 100,
      x: "-=350px",
      ease: "power4.inOut",
    });
    tl.to(
      ".sideBarBtn",
      {
        duration: 0.5,
        autoAlpha: 100,
        x: "-=250px",
        ease: "power4.inOut",
      },
      "finale"
    );
    sideDrawerOpen.value = true;
  } else {
    tl.add("finale");
    tl.to(".sideDrawer", {
      duration: 0.5,
      autoAlpha: 100,
      x: "+=350px",
      ease: "power4.inOut",
    });
    tl.to(
      ".sideBarBtn",
      {
        duration: 0.5,
        autoAlpha: 100,
        x: "+=250px",
        ease: "back.out(1.2)",
      },
      "finale"
    );
    sideDrawerOpen.value = false;
  }
}

function animateSearch() {
  if (!searchOpen.value) {
    tl.add("finale");
    tl.to(".search", {
      duration: 0.3,
      autoAlpha: 100,
      x: "+=400px",
      ease: "back.out(1)",
    });

    searchOpen.value = true;
  } else {
    tl.add("finale");
    tl.to(".search", {
      duration: 0.5,
      autoAlpha: 100,
      x: "-=400px",
      ease: "power4.inOut",
    });
    searchOpen.value = false;
  }
}

function getRandomInt(max) {
  return Math.floor(Math.random() * max);
}

//'left-['+getRandomInt(200)+'px]' 'top-['+getRandomInt(200)+'px]'

function randomLocation() {
  return "left:" + getRandomInt(4000) + "px; top:" + getRandomInt(4000) + "px";
}

function animateIntro() {
  console.log("animate intro");
  tl.to(
    ".search",
    {
      duration: 0.5,
      autoAlpha: 0.9,
      y: "-=59px",
      ease: "back.out(1.7)",
    },
    "finale"
  );
}
</script>
