<template>
  <UContainer
    class="sticky top-0 bg-accented border-b-2 border-neutral-300 flex items-center h-16 z-10"
  >
    <UContainer class="flex justify-between flex-wrap">
      <h3 class="font-bold text-xl">Sinan Elmas</h3>
      <div class="flex gap-2">
        <UButton
          color="neutral"
          variant="subtle"
          icon="i-devicon:github"
          label="GitHub Profil"
          href="https://github.com/elsinan"
        />
      </div>
    </UContainer>
  </UContainer>

  <UContainer
    class="sticky top-16 flex gap-2 items-center justify-center-safe bg-accented z-10 py-3 shadow-lg rounded-b-full"
  >
    <div v-for="item in items" :key="item.value">
      <UButton
        class="text-neutral-500 dark:text-neutral-400 hover:text-default"
        @click="item.value !== undefined && navigateToSection(String(item.value))"
        :icon="item.icon"
        :label="isMd ? item.label : ''"
        variant="link"
      >
      </UButton>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import type { TabsItem } from '@nuxt/ui'

const isMd = ref(window.innerWidth >= 768)
window.addEventListener('resize', () => {
  isMd.value = window.innerWidth >= 768
})

const items = ref<TabsItem[]>([
  {
    label: 'Links',
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
])

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
