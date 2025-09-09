<template>
  <UCard variant="subtle">
    <template #header> <div class="text-xl font-bold">Mein Werdegang</div></template>
    <UTimeline color="neutral" :default-value="1" :items="items"> </UTimeline>
  </UCard>
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
    slot: 'link' as const,
    link: 'https://www.htwk-leipzig.de',
  },
  {
    date: 'Sep 2021 - heute',
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
    description: "B.Sc. Informatik: 'Reinforcement Learning'",
    icon: 'i-lucide-graduation-cap',
    link: 'https://www.hs-mannheim.de',
  },
])
</script>
