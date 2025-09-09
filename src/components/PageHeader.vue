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
    class="sticky top-16 flex gap-5 items-center flex-wrap justify-center-safe bg-accented z-10 py-3 shadow-lg rounded-b-full"
  >
    <div v-for="item in items" :key="item.value">
      <UButton
        :class="[
          visibleTabs.includes(String(item.value))
            ? 'text-primary '
            : 'text-neutral-500  dark:text-neutral-400 hover:text-default',
        ]"
        @click="item.value !== undefined && navigateToSection(item.value)"
        :icon="item.icon"
        :label="item.label"
        variant="link"
      >
      </UButton>
    </div>
  </UContainer>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import type { TabsItem } from '@nuxt/ui'

const items = ref<TabsItem[]>([
  {
    label: 'Links',
    icon: 'i-lucide-link',
    value: 'introduction',
  },
  {
    label: 'Tech-Stack',
    icon: 'i-lucide-cpu',
    value: 'techstack',
  },
  {
    label: 'Werdegang',
    icon: 'i-lucide-scroll',
    value: 'werdegang',
  },
  {
    label: 'Projekte',
    icon: 'i-lucide-rocket',
    value: 'projekte',
  },
])

const visibleTabs = ref<string[]>(['introduction'])

import { onMounted, onBeforeUnmount, ref as vueRef, nextTick } from 'vue'

const sectionIds = (items.value as TabsItem[]).map((item) => String(item.value))
const contentContainer = vueRef<HTMLElement | null>(null)

const navigateToSection = (sectionId: string | number) => {
  const id = String(sectionId)
  const element = document.getElementById(id)
  if (element) {
    element.scrollIntoView({ behavior: 'smooth', block: 'start' })
  }
}

// Prüft, welche Sektionen im Container sichtbar sind
function getVisibleSectionsInContainer() {
  if (!contentContainer.value) return [sectionIds[0]]
  const containerRect = contentContainer.value.getBoundingClientRect()
  const visible: string[] = []
  for (const id of sectionIds) {
    const el = document.getElementById(id)
    if (el) {
      const rect = el.getBoundingClientRect()
      // Sichtbar, wenn irgendein Teil im Container sichtbar ist
      if (rect.bottom > containerRect.top && rect.top < containerRect.bottom) {
        visible.push(id)
      }
    }
  }
  return visible.length ? visible : [sectionIds[0]]
}

function onContainerScroll() {
  const visible = getVisibleSectionsInContainer()
  visibleTabs.value = visible
}

onMounted(() => {
  nextTick(() => {
    if (contentContainer.value) {
      contentContainer.value.addEventListener('scroll', onContainerScroll, { passive: true })
    }
  })
})
onBeforeUnmount(() => {
  if (contentContainer.value) {
    contentContainer.value.removeEventListener('scroll', onContainerScroll)
  }
})
</script>
