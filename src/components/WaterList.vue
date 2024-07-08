<script setup>
import { ref } from "vue";
const waterList = ref(localStorage.getItem("totalWater") ?? []);
</script>

<template>
  <ul v-if="waterList.length > 0" class="flex flex-col items-center justify-center w-1/3 gap-6 p-4 font-mono text-center"></ul>
  <span v-else class="flex items-center justify-center w-1/3 min-h-full text-xl text-center text-slate-800">Você ainda não bebeu água hoje.</span>
</template>
