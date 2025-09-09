<script setup lang="ts">
import { ref } from 'vue'
import HomePage from './views/HomePage.vue'
import type { TabsItem } from '@nuxt/ui'

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

<template>
  <UApp>
    <UContainer class="my-7 flex flex-col gap-7">
      <h3 class="font-bold text-xl">Sinan Elmas</h3>
      <UContainer class="flex flex-row gap-5">
        <div class="flex flex-col gap-1 min-w-[160px]">
          <div v-for="item in items" :key="item.value">
            <button
              class="group flex items-center w-full px-4 py-2 text-left border-l-2 transition-colors bg-transparent focus:outline-none"
              :class="[
                visibleTabs.includes(String(item.value))
                  ? 'border-primary text-primary font-semibold bg-primary-50'
                  : 'border-transparent text-gray-700 hover:bg-primary-50 hover:text-primary',
              ]"
              @click="item.value !== undefined && navigateToSection(item.value)"
            >
              <span v-if="item.icon" :class="item.icon + ' mr-2 text-lg'" />
              <span>{{ item.label }}</span>
            </button>
          </div>
        </div>
        <div class="flex-1 overflow-auto" style="max-height: 80vh" ref="contentContainer">
          <HomePage />
        </div>
      </UContainer>
    </UContainer>
  </UApp>
</template>
