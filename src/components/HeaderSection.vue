<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { ref } from 'vue'
import logo from '@/assets/eurocredit_logo.png'
import Button from './ui/UiButton.vue'
import HeaderMenu from './HeaderMenu.vue'
import LanguageSwitcher from './LanguageSwitcher.vue'

const { t } = useI18n()
const isMobileMenuOpen = ref(false)

const toggleMobileMenu = () => {
  isMobileMenuOpen.value = !isMobileMenuOpen.value
}

const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
</script>

<template>
  <header class="mx-auto flex flex-col items-center leading-3.5">
    <div class="flex w-full max-w-[1440px] justify-between p-5 sm:px-12.5 sm:py-3 lg:px-28 lg:py-6">
      <div class="flex items-center">
        <img alt="Vue logo" :src="logo" />
        <div class="mx-4 hidden h-12 w-px bg-neutral-200 md:block lg:mx-8"></div>
        <div class="hidden md:flex">
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
          <Button class="hidden md:block" size="medium" variant="primary">{{
            t('header.CTA')
          }}</Button>

          <Button
            variant="icon"
            class="w-full border border-solid border-neutral-200 md:hidden"
            @click="toggleMobileMenu"
          >
            <i :class="isMobileMenuOpen ? 'pi pi-times' : 'pi pi-bars'" class="p-1 text-lg"></i>
          </Button>
        </div>
      </div>
    </div>

    <div class="hidden w-full md:block">
      <HeaderMenu />
    </div>

    <div v-if="isMobileMenuOpen" class="fixed inset-0 z-50 md:hidden" @click="closeMobileMenu">
      <div class="bg-opacity-50 fixed inset-0 transition-opacity duration-300"></div>

      <div
        class="absolute top-[150px] right-0 left-0 h-full transform border-t border-neutral-200 bg-white shadow-xl transition-all duration-300 ease-in-out"
        :class="isMobileMenuOpen ? 'translate-y-0 opacity-100' : '-translate-y-full opacity-0'"
        @click.stop
      >
        <div class="p-5">
          <nav>
            <ul class="space-y-4">
              <li
                v-for="(item, index) in [
                  { name: t('header.menu.autoLoan'), href: '#' },
                  { name: t('header.menu.businessLoan'), href: '#' },
                  { name: t('header.menu.selfEmployedLoan'), href: '#' },
                  { name: t('header.menu.aboutUs'), href: '#' },
                  { name: t('header.menu.blog'), href: '#' },
                  { name: t('header.menu.contact'), href: '#' },
                ]"
                :key="index"
              >
                <a
                  :href="item.href"
                  class="font-firago hover:text-brand-dark-blue block border-b border-neutral-100 py-3 text-base font-medium text-neutral-700 last:border-b-0"
                  @click="closeMobileMenu"
                >
                  {{ item.name }}
                </a>
              </li>
            </ul>
          </nav>
          <hr class="my-6 border-neutral-100" />
          <div class="mb-6 space-y-4">
            <Button
              size="medium"
              class="w-full shadow-sm transition-shadow duration-200 hover:shadow-md"
            >
              <a
                href="#request-loan"
                @click="closeMobileMenu"
                class="flex items-center justify-center gap-2"
              >
                <i class="pi pi-calculator text-sm"></i>
                {{ t('header.CTA') }}
              </a>
            </Button>

            <Button
              class="w-full border border-neutral-200 bg-white shadow-sm transition-colors duration-200 hover:bg-neutral-50 hover:shadow-md"
              size="medium"
            >
              <a
                href="#login"
                class="hover:text-brand-dark-blue flex items-center justify-center gap-2 text-neutral-700 transition-colors duration-200"
                @click="closeMobileMenu"
              >
                <i class="pi pi-user text-sm"></i>
                <span class="font-medium">შესვლა</span>
              </a>
            </Button>
          </div>

          <div class="rounded-lg border border-neutral-100 bg-neutral-50 p-4">
            <div class="flex items-center justify-center gap-3">
              <div class="bg-brand-dark-blue/10 rounded-full p-2">
                <i class="pi pi-phone text-brand-dark-blue text-sm"></i>
              </div>
              <div class="text-center">
                <p class="mb-1 text-xs text-neutral-500">ზარის ცენტრი</p>
                <a
                  href="tel:+995555624421"
                  class="font-firago hover:text-brand-dark-blue text-sm font-semibold text-neutral-700 transition-colors duration-200"
                >
                  +995 555 62 44 21
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </header>
</template>
