<script setup lang="ts">
import LoanSlider from './LoanSlider.vue'
import Button from './ui/UiButton.vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()
</script>

<template>
  <div
    class="mx-auto my-20 flex w-full max-w-[1200px] flex-col items-center rounded-[48px] bg-neutral-100 px-5 py-10 md:my-24 md:px-28 md:py-12 lg:my-32"
    id="request-loan"
  >
    <h1
      class="font-firago text-center text-3xl leading-normal font-bold tracking-[-0.216px] text-neutral-800 md:text-4xl"
    >
      {{ t('loan.heading') }}
    </h1>
    <p class="font-abeezee mt-2 mb-7 text-center text-base leading-7 font-normal text-neutral-700">
      {{ t('loan.subheading') }}
    </p>
    <div class="flex w-full max-w-[450px] flex-col">
      <div class="mb-1 flex justify-between">
        <span class="font-firago text-sm font-semibold text-neutral-700">{{
          t('loan.howMuch')
        }}</span>
        <span class="font-abeezee text-right text-xs font-normal text-neutral-500"
          >{{ t('loan.max') }}: 24 000₾</span
        >
      </div>
      <LoanSlider />
      <Button class="mt-11">{{ t('loan.button') }}</Button>
    </div>
  </div>
</template>
