<template>
  <UContainer
    class="sticky top-0 bg-accented border-b-2 border-neutral-300 flex items-center h-16 z-10"
  >
    <h3 class="font-bold text-xl">Sinan Elmas</h3>
  </UContainer>

  <UContainer
    class="sticky top-16 flex gap-5 items-center justify-center-safe bg-accented z-10 py-3 shadow-lg rounded-b-full"
  >
    <div v-for="item in items" :key="item.value">
      <UButton
        class="text-neutral-500 dark:text-neutral-400 hover:text-default hover:"
        :icon="item.icon"
        :label="isMd ? item.label : ''"
        @click="item.value !== undefined && navigateToSection(String(item.value))"
        variant="link"
      >
      </UButton>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const isMd = ref(window.innerWidth >= 768)

window.addEventListener('resize', () => {
  isMd.value = window.innerWidth >= 768
})

const items = [
  {
    label: 'Kontakt',
    icon: 'i-lucide-link',
    value: 'introduction',
  },
  {
    label: 'Werdegang',
    icon: 'i-lucide-scroll',
    value: 'werdegang',
  },
  {
    label: 'Tech-Stack',
    icon: 'i-lucide-cpu',
    value: 'techstack',
  },
  {
    label: 'Projekte',
    icon: 'i-lucide-rocket',
    value: 'projekte',
  },
]

function navigateToSection(sectionId: string) {
  const el = document.getElementById(sectionId)
  if (el) {
    const headerOffset = 140
    const elementPosition = el.getBoundingClientRect().top + window.pageYOffset
    const offsetPosition = elementPosition - headerOffset
    window.scrollTo({
      top: offsetPosition,
      behavior: 'smooth',
    })
  }
}
</script>
