<template>
  <UTimeline color="neutral" :default-value="1" :items="items" class="w-96"> </UTimeline>
</template>

<script setup lang="ts">
import type { TimelineItem } from '@nuxt/ui'
import { ref } from 'vue'
const items = ref<TimelineItem[]>([
  {
    date: 'Okt 2022 - heute',
    title: 'HTWK Leipzig',
    description: "M.Sc. Informatik: 'ConsentServer:'",
    icon: 'i-lucide-graduation-cap',
  },
  {
    date: 'Sep 2021 - heute',
    title: 'SV SparkassenVersicherung Lebensversicherung AG',
    description: 'Werkstudent',
    icon: 'i-lucide-code',
  },
  {
    date: 'Apr 2021 - Sep 2021',
    title: 'SV SparkassenVersicherung Lebensversicherung AG',
    description: 'Pflichtpraktikum',
    icon: 'i-lucide-code',
  },
  {
    date: 'Sept 2018 bis Nov 2022',
    title: 'Technische Hochschule Mannheim',
    description: "B.Sc. Informatik: 'Reinforcement Learning'",
    icon: 'i-lucide-graduation-cap',
  },
  {
    date: 'Apr 5 2025',
    title: 'Testing & Deployment',
    description: 'QA testing and performance optimization. Deployed the application to production.',
    icon: 'i-lucide-check-circle',
  },
])
</script>
