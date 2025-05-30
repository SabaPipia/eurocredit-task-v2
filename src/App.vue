<script setup lang="ts">
import Header from './components/HeaderSection.vue'
import PromoSection from './components/PromoSection.vue'
import HeroSection from './components/HeroSection.vue'
import LoanSection from './components/LoanSection.vue'
</script>

<template>
  <PromoSection />
  <Header />

  <main
    class="xs:px-8.5 xs:py-5 mx-auto mt-7 flex w-full max-w-[1440px] flex-col items-center justify-between gap-7 p-5 sm:px-12.5 sm:py-3 md:mt-10 md:gap-10 lg:gap-16 lg:px-28 lg:py-6 xl:flex-row"
  >
    <HeroSection />
    <LoanSection />
  </main>
</template>
