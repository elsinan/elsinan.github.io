<template>
  <UCard variant="subtle" class="h-min">
    <template #header>
      <span class="font-semibold">Technologien & Tools, mit denen ich schon gearbeitet habe</span>
    </template>
    <div class="flex flex-wrap gap-2">
      <div v-for="tech in technologies" :key="tech.icon">
        <UBadge
          color="neutral"
          variant="subtle"
          :icon="tech.icon"
          size="lg"
          :label="tech.label"
          class="not-hover:grayscale dark:not-hover:brightness-105 not-hover:brightness-95"
        />
      </div>
    </div>
  </UCard>
</template>

<script setup lang="ts">
import { technologies } from '@/data/technologies'
</script>
