<template>
  <div class="flex flex-col gap-5 border-3 shadow-lg border-accented rounded-lg p-6">
    <div class="flex justify-between items-start gap-5">
      <div class="flex gap-3 flex-wrap items-center">
        <div class="text-lg font-bold">{{ title }}</div>
        <div v-if="ongoing"><UBadge variant="soft" label="ongoing" /></div>
      </div>
      <UButton
        v-if="projectLink"
        label="Link"
        :to="projectLink"
        color="neutral"
        variant="outline"
        trailing-icon="i-lucide-external-link"
      />
    </div>
    <div class="flex flex-col gap-5 lg:flex-row">
      <UCarousel
        v-if="images"
        v-slot="{ item }"
        :items="images"
        align="end"
        class="m-1 w-fit h-fit"
      >
        <img
          v-if="item"
          :src="`https://raw.githubusercontent.com/elsinan/elsinan.github.io/refs/heads/main/src/assets/${item.src}`"
          class="border-2 border-accented rounded-lg overflow-clip"
          :width="`${item.scale}%`"
          :style="contentHeight ? { 'max-height': contentHeight * 1.5 } : ''"
        />
      </UCarousel>
      <div :id="`${title}Content`" class="flex flex-col gap-3 h-min">
        <div>{{ description }}</div>
        <div v-if="usedTechnologies" class="flex flex-wrap gap-2">
          <div v-for="technology in usedTechnologies" :key="technology">
            <UBadge
              color="neutral"
              variant="subtle"
              size="sm"
              v-if="technologies.find((entry) => entry.label === technology)"
              :icon="technologies.find((entry) => entry.label === technology)?.icon"
              :label="technologies.find((entry) => entry.label === technology)?.label"
              class="not-hover:grayscale dark:not-hover:brightness-105 not-hover:brightness-95 cursor-default"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref, watch, nextTick } from 'vue'
import { technologies } from '@/data/technologies'
const props = defineProps<{
  images?: { src: string; scale: string }[]
  title: string
  description: string
  ongoing?: boolean
  githubLink?: string
  projectLink?: string
  usedTechnologies?: string[]
}>()

const contentHeight = ref<number | null>(null)

function updateContentHeight() {
  const el = document.getElementById(`${props.title}Content`)
  contentHeight.value = el ? el.offsetHeight : null
}

onMounted(() => {
  updateContentHeight()
})

watch(
  () => props.title,
  async () => {
    await nextTick()
    updateContentHeight()
  },
)
</script>
