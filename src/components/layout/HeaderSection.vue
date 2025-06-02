<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { computed } from 'vue'
import logo from '@/assets/eurocredit_logo.png'
import Button from '../ui/UiButton.vue'
import HeaderMenu from './HeaderMenu.vue'
import LanguageSwitcher from './LanguageSwitcher.vue'
import BurgerMenu from './BurgerMenu.vue'

const { t } = useI18n()

const menuItems = computed(() => [
  { name: t('header.menu.autoLoan'), href: '#' },
  { name: t('header.menu.businessLoan'), href: '#' },
  { name: t('header.menu.selfEmployedLoan'), href: '#' },
  { name: t('header.menu.aboutUs'), href: '#' },
  { name: t('header.menu.blog'), href: '#' },
  { name: t('header.menu.contact'), href: '#' },
])
</script>

<template>
  <header class="mx-auto flex flex-col items-center border-b border-neutral-100 leading-3.5">
    <div
      class="xs:py-5 flex w-full max-w-[1440px] justify-between px-8 py-5 sm:px-12.5 sm:py-3 lg:px-28 lg:py-6"
    >
      <div class="flex items-center">
        <img alt="Vue logo" class="size-9/12 sm:size-auto" :src="logo" />
        <div class="mx-4 hidden h-12 w-px bg-neutral-200 md:block lg:mx-8"></div>
        <div class="hidden md:flex">
          <i class="pi pi-phone text-lg"></i>
          <a
            href="tel:+995555624421"
            class="font-firago ml-1.5 text-sm leading-normal font-medium text-neutral-700"
          >
            +995 555 62 44 21
          </a>
        </div>
      </div>

      <div class="flex items-center gap-4 lg:gap-8">
        <LanguageSwitcher />

        <div class="flex gap-2">
          <Button variant="icon" class="hidden border border-solid border-neutral-200 sm:block">
            <i class="pi pi-user p-1 text-lg"></i>
          </Button>
          <a href="#request-loan" class="flex w-fit">
            <Button class="hidden md:block" size="medium" variant="primary">{{
              t('header.CTA')
            }}</Button>
          </a>

          <BurgerMenu :menu-items="menuItems" />
        </div>
      </div>
    </div>

    <div class="hidden w-full md:block">
      <HeaderMenu />
    </div>
  </header>
</template>
