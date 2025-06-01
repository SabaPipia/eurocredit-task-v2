<script setup lang="ts">
import heroImg from '@/assets/hero_img.png'
import Button from '../ui/UiButton.vue'
import heroCheck from '@/assets/check_icon.png'
import { useI18n } from 'vue-i18n'
import { computed } from 'vue'
import Image from 'primevue/image'

const { t } = useI18n()

const BENEFITS = computed(() => [
  t('hero.benefits.1'),
  t('hero.benefits.2'),
  t('hero.benefits.3'),
  t('hero.benefits.4'),
])
</script>

<template>
  <section class="flex w-full flex-col items-center justify-between gap-10 xl:flex-row xl:gap-7">
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
        <a href="#request-loan" class="flex w-fit">
          <Button variant="primary">
            {{ t('hero.button') }}
          </Button>
        </a>
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
    <div class="flex w-full justify-center">
      <Image :src="heroImg" alt="" />
    </div>
  </section>
</template>
