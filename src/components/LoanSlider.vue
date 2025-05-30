<script setup lang="ts">
import { ref, computed } from 'vue'

const sliderValue = ref(12500)
const min = 1000
const max = 24000

// Computed percentage for CSS custom property
const percentage = computed(() => ((sliderValue.value - min) / (max - min)) * 100)
</script>

<template>
  <div class="relative">
    <input
      v-model="sliderValue"
      type="range"
      :min="min"
      :max="max"
      step="50"
      class="slider h-[17px] w-full appearance-none rounded-[96px] outline-none"
      :style="{ '--fill-percentage': percentage + '%' }"
    />
    <div
      class="font-abeezee border-stroke-soft-200 text-main-900 absolute -translate-x-1/2 rounded-[4px] border bg-white p-1 text-center text-xs"
      :style="{ left: percentage + '%', top: '35px' }"
    >
      {{ sliderValue.toLocaleString() }}₾
      <img
        class="absolute top-[2.5px] left-1/2 -translate-x-1/2 -translate-y-full"
        src="@/assets/Tail.svg"
        alt=""
      />
    </div>
  </div>
</template>

<style scoped>
.slider {
  background: linear-gradient(
    to right,
    #1a3364 0%,
    #1a3364 var(--fill-percentage),
    #e2e4e9 var(--fill-percentage),
    #e2e4e9 100%
  );
}

.slider::-webkit-slider-thumb {
  -webkit-appearance: none;
  appearance: none;
  width: 25px;
  height: 25px;
  cursor: pointer;
  border-radius: 50%;
  background: #1a3364;
  border: 7px solid #ffffff;
  position: relative;
  transition: 0.3s;
}

.slider::-webkit-slider-thumb:active {
  transform: scale(1.1);
}
</style>
