<script setup>
import Form from "./components/Form.vue";
import Glass from "./components/Glass.vue";
import WaterList from "./components/WaterList.vue";
</script>
<template>
  <div class="flex items-center justify-between w-full min-h-screen p-6 bg-slate-950">
    <div class="flex w-full border border-slate-800 rounded-2xl">
      <Form />
      <WaterList />
      <Glass />
    </div>
  </div>
</template>
