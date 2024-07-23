<script setup lang="ts">
import IconCaret from "./IconCaret.vue";
import IconBurger from "./IconBurger.vue";
const props = defineProps(["open"]);
</script>

<template>
  <div
    class="border border-zinc-300 rounded-full min-w-12 min-h-12 flex justify-center items-center z-50 cursor-pointer"
    :class="
      !open
        ? 'bg-green-600 shadow-lg hover:bg-green-700'
        : 'bg-zinc-200 hover:bg-zinc-100'
    "
  >
    <IconBurger v-if="!open" class="text-3xl text-white" />
    <IconCaret v-else class="text-5xl text-green-600 rotate-90" />
  </div>
</template>
