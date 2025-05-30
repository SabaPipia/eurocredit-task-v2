<script setup lang="ts">
import { useI18n } from 'vue-i18n'
import Button from './ui/UiButton.vue'

const { t } = useI18n()
</script>

<template>
  <div
    class="font-firago bg-brand-dark-blue text-neutral-0 flex items-center justify-center gap-4 px-1 py-3 text-center text-sm leading-normal font-semibold"
  >
    <span>
      {{ t('promo') }}
    </span>
    <Button variant="icon">
      <i class="pi pi-arrow-right" style="color: white"></i>
    </Button>
  </div>
</template>
