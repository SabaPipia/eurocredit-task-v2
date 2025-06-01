<template>
  <Button
    variant="icon"
    class="w-full border border-solid border-neutral-200 md:hidden"
    @click="toggleMenu"
  >
    <i :class="isOpen ? 'pi pi-times' : 'pi pi-bars'" class="p-1 text-lg"></i>
  </Button>

  <div v-if="isOpen" class="fixed inset-0 z-50 md:hidden" @click="closeMenu">
    <div class="bg-opacity-50 fixed inset-0 transition-opacity duration-300"></div>

    <div
      class="absolute top-[150px] right-0 left-0 max-h-[calc(100vh-150px)] transform overflow-y-auto border-t border-neutral-200 bg-white shadow-xl transition-all duration-300 ease-in-out sm:top-[130px] sm:max-h-[calc(100vh-130px)] md:top-[150px] md:max-h-[calc(100vh-150px)]"
      :class="isOpen ? 'translate-y-0 opacity-100' : '-translate-y-full opacity-0'"
      @click.stop
    >
      <div class="xs:px-8.5 xs:py-5 p-5 sm:px-12.5 sm:py-3">
        <nav>
          <ul class="space-y-4">
            <li v-for="(item, index) in menuItems" :key="index">
              <a
                :href="item.href"
                class="font-firago hover:text-brand-dark-blue block border-b border-neutral-100 py-3 text-base font-medium text-neutral-700 last:border-b-0"
                @click="closeMenu"
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
              @click="closeMenu"
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
              @click="closeMenu"
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
</template>

<script setup lang="ts">
import { ref, onUnmounted } from 'vue'
import Button from '../ui/UiButton.vue'
import { useI18n } from 'vue-i18n'

const { t } = useI18n()

interface MenuItem {
  name: string
  href: string
}

interface Props {
  menuItems: MenuItem[]
}

defineProps<Props>()

const isOpen = ref(false)

const lockBodyScroll = () => {
  document.body.style.overflow = 'hidden'
  document.body.style.paddingRight = '0px' // Prevent layout shift
}

const unlockBodyScroll = () => {
  document.body.style.overflow = ''
  document.body.style.paddingRight = ''
}

const toggleMenu = () => {
  isOpen.value = !isOpen.value

  if (isOpen.value) {
    lockBodyScroll()
  } else {
    unlockBodyScroll()
  }
}

const closeMenu = () => {
  isOpen.value = false
  unlockBodyScroll()
}

onUnmounted(() => {
  if (isOpen.value) {
    unlockBodyScroll()
  }
})
</script>
