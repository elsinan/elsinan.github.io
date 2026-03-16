<template>
  <UCard variant="subtle">
    <template #header> <div class="text-xl font-bold">Mein Werdegang</div></template>
    <UTimeline color="neutral" :default-value="0" :items="items"> </UTimeline>
  </UCard>
</template>

<script setup lang="ts">
import type { TimelineItem } from '@nuxt/ui'
import { ref } from 'vue'
const items = ref<TimelineItem[]>([
  {
    date: 'Apr 2026',
    title: '???',
    description: 'Auf der Suche nach der nächsten Herausforderung',
    icon: 'i-lucide-circle-question-mark',
    slot: 'link' as const,
    link: 'https://www.htwk-leipzig.de',
  },
  {
    date: 'Okt 2022 - Jan 2026',
    title: 'HTWK Leipzig',
    description: 'M.Sc. Informatik: Abschlussthema Consent Management',
    icon: 'i-lucide-graduation-cap',
    link: 'https://www.htwk-leipzig.de',
  },
  {
    date: 'Sep 2021 - Dez 2025',
    title: 'SV SparkassenVersicherung Lebensversicherung AG',
    description: 'Werkstudent',
    icon: 'i-lucide-code',
    link: 'https://www.sparkassenversicherung.de',
  },
  {
    date: 'Apr 2021 - Sep 2021',
    title: 'SV SparkassenVersicherung Lebensversicherung AG',
    description: 'Pflichtpraktikum',
    icon: 'i-lucide-code',
    link: 'https://www.sparkassenversicherung.de',
  },
  {
    date: 'Sep 2018 bis Nov 2022',
    title: 'Technische Hochschule Mannheim',
    description: 'B.Sc. Informatik: Abschlussthema Reinforcement Learning',
    icon: 'i-lucide-graduation-cap',
    link: 'https://www.hs-mannheim.de',
  },
])
</script>
