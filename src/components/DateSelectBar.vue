<script setup>
import { ref } from "vue";
import { useBudgetStore } from "../store";

const store = useBudgetStore();

const dates = Object.keys(store.spendings);
</script>

<template>
  <div class="px-1">
    <div
      class="rounded-xl border-dashed mt-1 py-[7px] px-1 border-2 border-cyan-500 flex flex-row overflow-x-auto lg:small-scrollbar xl:small-scrollbar md:scrollbar sm:scrollbar scrollbar"
    >
      <div
        v-for="date in dates"
        class="flex-none w-32"
      >
        <input
          type="radio"
          :id="date"
          :value="date"
          :checked="date == store.selectedDate"
          v-model="store.selectedDate"
          class="peer hidden"
        />
        <label
          :for="date"
          class="font-bold cursor-pointer select-none rounded-lg py-1 px-3 text-center peer-checked:bg-cyan-500 text-slate-700 peer-checked:text-white"
          >{{ date }}
        </label>
      </div>
    </div>
  </div>
</template>
