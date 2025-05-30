<template>
  <button
    :class="
      cn(
        'font-firago flex items-center justify-center gap-2 border-none text-sm',
        variant === 'primary' && 'bg-brand-dark-blue rounded-full text-white',
        variant === 'icon' && 'rounded-full bg-white/30 p-2.5 text-black',
        variant !== 'icon' && size === 'large' && 'px-6.5 py-4.5 font-medium',
        variant !== 'icon' && size === 'medium' && 'px-4.5 py-3.5 font-medium',
        variant !== 'icon' && size === 'small' && 'px-2.5 py-2.5 font-normal',
        customClass,
      )
    "
    :type="type === 'button' || type === 'submit' || type === 'reset' ? type : 'button'"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
import type { PropType } from 'vue'
import { cn } from '@/utils/cn'

defineProps({
  variant: {
    type: String,
    default: 'primary',
  },
  size: {
    type: String as PropType<'large' | 'medium' | 'small'>,
    default: 'large',
  },
  type: {
    type: String,
    default: 'button',
  },
  customClass: {
    type: String,
    default: '',
  },
})
</script>
