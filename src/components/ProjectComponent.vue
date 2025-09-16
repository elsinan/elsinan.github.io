<template>
  <div class="flex flex-col gap-5 border-3 shadow-lg border-accented rounded-lg p-5">
    <div class="flex justify-between items-center">
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
    <div class="flex gap-5 flex-col md:flex-row">
      <UCarousel
        v-if="imageSrcs"
        v-slot="{ item }"
        :items="imageSrcs"
        align="center"
        auto-height
        class="m-1"
      >
        <img
          v-if="item"
          :src="item"
          class="border border-2 border-accented rounded-lg overflow-clip"
      /></UCarousel>
      <div class="flex flex-col gap-2">
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
              class="not-hover:grayscale dark:not-hover:brightness-105 not-hover:brightness-95"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { technologies } from '@/data/technologies'
defineProps<{
  imageSrcs?: string[]
  title: string
  description: string
  ongoing?: boolean
  githubLink?: string
  projectLink?: string
  usedTechnologies?: string[]
}>()
</script>
