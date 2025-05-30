<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import { computed } from 'vue'

const { t } = useI18n()

const NAVITEMS = computed(() => [
  { name: t('header.menu.autoLoan'), href: '#' },
  { name: t('header.menu.businessLoan'), href: '#' },
  { name: t('header.menu.selfEmployedLoan'), href: '#' },
  { name: t('header.menu.aboutUs'), href: '#' },
  { name: t('header.menu.blog'), href: '#' },
  { name: t('header.menu.contact'), href: '#' },
])
</script>

<template>
  <nav class="flex w-full justify-center bg-neutral-100 p-5 sm:px-12.5 sm:py-6 lg:px-28 lg:py-6">
    <div>
      <ul class="m-0 flex list-none flex-wrap justify-center gap-x-10 gap-y-5 p-0">
        <a class="text-decoration-none" href="#" v-for="(item, index) in NAVITEMS" :key="index">
          <li
            class="font-firago hover:text-brand-dark-blue text-sm leading-normal font-medium text-neutral-700 hover:underline"
          >
            {{ item.name }}
          </li>
        </a>
      </ul>
    </div>
  </nav>
</template>
