<script setup>
import { ref } from "vue";

const formatter = new Intl.NumberFormat("pt-BR", {
  currency: "BRL",
});

const total = ref(0);
const setWeight = ref();
const setWater = ref();

const setTotal = (weight) => {
  return (total.value = weight * 35);
};
</script>

<template>
  <div class="flex flex-col items-center justify-center w-1/3 gap-6 p-4 font-mono text-center">
    <div class="flex flex-col w-full gap-6 p-6 border shadow-md border-slate-800 rounded-2xl">
      <span class="text-2xl text-slate-200">Quanto de água eu preciso?</span>
      <div class="flex gap-2">
        <input v-model="setWeight" placeholder="Seu peso aqui..." class="block w-full text-center rounded-lg shadow-sm border-slate-300 focus:border-slate-200 focus:ring-slate-200 dark:bg-slate-900 dark:border-transparent dark:text-slate-200" type="number" />
        <button
          @click="
            () => {
              setTotal(setWeight);
            }
          "
          :disabled="!setWeight || setWeight <= 0"
          class="h-[42px] px-4 py-2 text-xs font-semibold leading-tight tracking-widest text-slate-600 uppercase transition duration-150 ease-in-out bg-transparent border border-slate-800 disabled:cursor-not-allowed rounded-lg hover:bg-slate-900 flex items-center justify-center"
          type="button"
        >
          Descobrir
        </button>
      </div>
      <div class="block w-full p-2 rounded-lg shadow-sm border-slate-300 focus:border-slate-200 focus:ring-slate-200 dark:bg-slate-900 dark:border-transparent dark:text-slate-200">{{ formatter.format(total.toFixed(2)) }} ml</div>
    </div>
    <div class="flex flex-col w-full gap-6 p-6 border shadow-md border-slate-800 rounded-2xl">
      <span class="text-2xl text-slate-200">Quanto eu já bebi?</span>
      <div class="flex gap-2">
        <input v-model="setWater" placeholder="Quantidade em ml..." class="block w-full text-center rounded-lg shadow-sm bg-slate-100 border-slate-300 focus:border-slate-200 focus:ring-slate-200 dark:bg-slate-900 dark:border-transparent dark:text-slate-200" type="number" />
        <button
          @click="
            () => {
              localStorage.setItem('totalWater', setWater);
            }
          "
          class="h-[42px] px-4 py-2 text-xs font-semibold leading-tight tracking-widest text-slate-600 uppercase transition duration-150 ease-in-out bg-transparent border border-slate-800 disabled:cursor-not-allowed rounded-lg hover:bg-slate-900 flex items-center justify-center"
          type="button"
        >
          Adicionar
        </button>
      </div>
      <div class="block w-full max-w-xl p-2 rounded-lg shadow-sm bg-slate-100 border-slate-300 focus:border-slate-200 focus:ring-slate-200 dark:bg-slate-900 dark:border-transparent dark:text-slate-200">{{ formatter.format(total.toFixed(2)) }} ml</div>
    </div>
  </div>
</template>
