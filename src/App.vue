<script setup lang="ts">
import Header from './components/layout/HeaderSection.vue'
import PromoSection from './components/sections/PromoSection.vue'
import HeroSection from './components/sections/HeroSection.vue'
import LoanSection from './components/sections/LoanSection.vue'

document.title = 'ევროკრედიტი'
</script>

<template>
  <PromoSection />
  <Header />

  <main
    class="mx-auto mt-7 flex w-full max-w-[1440px] flex-col px-8 sm:px-12.5 sm:py-3 md:mt-10 md:gap-10 lg:gap-16 lg:px-28 lg:py-6"
  >
    <HeroSection />
    <LoanSection />
  </main>
</template>
