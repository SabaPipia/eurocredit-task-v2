<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import logo from '@/assets/eurocredit_logo.png'
import Button from './ui/UiButton.vue'
import HeaderMenu from './HeaderMenu.vue'
import LanguageSwitcher from './LanguageSwitcher.vue'

const { t } = useI18n()
</script>

<template>
  <header class="mx-auto flex flex-col items-center leading-3.5">
    <div class="flex w-full max-w-[1440px] justify-between p-5 sm:px-12.5 sm:py-3 lg:px-28 lg:py-6">
      <div class="flex items-center">
        <img alt="Vue logo" class="hidden lg:block" :src="logo" />
        <div class="mx-8 hidden h-12 w-px bg-neutral-200 lg:block"></div>
        <div class="flex">
          <i class="pi pi-phone text-lg"></i>
          <span class="font-firago ml-1.5 text-sm leading-normal font-medium text-neutral-700">
            +995 555 62 44 21
          </span>
        </div>
      </div>
      <div class="flex items-center gap-8">
        <LanguageSwitcher />
        <div class="flex gap-2">
          <Button variant="icon" class="border border-solid border-neutral-200">
            <i class="pi pi-user p-1 text-lg"></i>
          </Button>
          <Button class="hidden sm:block" size="medium" variant="primary">{{
            t('header.CTA')
          }}</Button>
        </div>
      </div>
    </div>
    <HeaderMenu />
  </header>
</template>
