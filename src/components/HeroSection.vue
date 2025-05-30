<script setup lang="ts">
import heroImg from '@/assets/hero_img.png'
import Button from './ui/UiButton.vue'
import heroCheck from '@/assets/check_icon.png'
import { useI18n } from 'vue-i18n'
import { computed } from 'vue'

const { t } = useI18n()

const BENEFITS = computed(() => [
  t('hero.benefits.1'),
  t('hero.benefits.2'),
  t('hero.benefits.3'),
  t('hero.benefits.4'),
])
</script>

<template>
  <section
    class="xs:px-8.5 xs:py-5 mx-auto mt-0 flex max-w-[1200px] flex-col justify-between gap-16 p-5 sm:px-12.5 sm:py-3 md:mt-10 lg:px-28 lg:py-6 xl:flex-row"
  >
    <div class="flex flex-col justify-center">
      <h1
        class="font-firago xs:text-2xl mb-2 text-xl leading-normal font-semibold text-neutral-800 sm:mb-4 md:text-4xl md:leading-[54px] md:font-bold lg:text-[42px]"
      >
        {{ t('hero.heading') }}
      </h1>
      <p class="font-abeezee xs:text-lg mb-6 text-base leading-7 font-normal text-neutral-700">
        {{ t('hero.subheading') }}
      </p>

      <div class="mb-6 md:mb-11">
        <Button variant="primary">{{ t('hero.button') }}</Button>
      </div>

      <ul class="flex list-none flex-col gap-4 p-0">
        <li
          class="font-abeezee flex items-center gap-4 text-base text-gray-600"
          v-for="(benefit, index) in BENEFITS"
          :key="index"
        >
          <img :src="heroCheck" alt="" />
          {{ benefit }}
        </li>
      </ul>
    </div>
    <img class="hero-img w-full lg:w-4/5 xl:m-5 xl:w-1/2" :src="heroImg" alt="" />
  </section>
</template>
