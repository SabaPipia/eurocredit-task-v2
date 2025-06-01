<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import geoFlag from '@/assets/geo_flag.jpg'
import enFlag from '@/assets/united-kingdom_flag.png'

const { locale, t } = useI18n()

const toggleLanguage = () => {
  locale.value = locale.value === 'en' ? 'ka' : 'en'
}
</script>

<template>
  <div class="language-switcher flex cursor-pointer items-center gap-1.5" @click="toggleLanguage">
    <span class="font-firago text-sm leading-normal text-neutral-700">{{
      t('header.language')
    }}</span>
    <img
      class="size-5 rounded-full object-cover"
      :src="locale === 'ka' ? geoFlag : enFlag"
      alt="language_flag"
    />
  </div>
</template>
