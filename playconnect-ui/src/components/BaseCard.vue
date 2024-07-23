<template>
  <div
    class="opacity-0 shadow-md fixed z-40 top-[80px] left-4 w-96 rounded-md bg-zinc-200 border border-zinc-600"
  >
    <div class="w-full border-b border-zinc-600">
      <div class="p-0 flex flex-row">
        <input
          v-focus
          type="text"
          placeholder="Search vehicles"
          class="text-xl bg-zinc-200 focus:outline-none w-full p-3 border-0 rounded-t-md focus:text-zinc-100 focus:bg-zinc-700 pl-12"
        />
      </div>
    </div>
    <div class="p-3 min-h-80"></div>
    <div class="p-3 w-full border-t border-zinc-600 min-h-14"></div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const props = defineProps(["open"]);
const focus = ref(false);
defineEmits("showhide");

const vFocus = {
  mounted: (el) => el.focus(),
};
</script>
