<script setup lang="ts">
import { ref } from "vue";
import IconCaret from "./IconCaret.vue";
import IconSearch from "./IconSearch.vue";
const props = defineProps(["open"]);
const hover = ref(false);
</script>

<template>
  <div
    @mouseenter="hover = true"
    @mouseleave="hover = false"
    class="rounded-full min-w-12 min-h-12 flex justify-center items-center z-50 cursor-pointer"
    :class="!open ? 'bg-green-600 hover:bg-green-700' : 'bg-transparent'"
  >
    <IconSearch
      v-if="!hover"
      class="text-3xl text-zinc-100 hover:text-green-600"
      :class="!open ? 'text-zinc-100' : 'text-zinc-400'"
    />
    <IconCaret
      v-else
      class="text-5xl text-zinc-300"
      :class="open ? '-rotate-90' : 'rotate-90'"
    />
  </div>
</template>
