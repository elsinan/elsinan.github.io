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
const technologies = [
  { icon: 'i-devicon:csharp', label: 'C#' },
  { icon: 'i-devicon:eslint', label: 'ESLint' },
  { icon: 'i-devicon:docker', label: 'Docker' },
  { icon: 'i-devicon:git', label: 'Git' },
  { icon: 'i-devicon:github', label: 'GitHub' },
  { icon: 'i-devicon:gitlab', label: 'GitLab' },
  { icon: 'i-devicon:jira', label: 'Jira' },
  { icon: 'i-devicon:nodejs', label: 'Node.js' },
  { icon: 'i-devicon:nuxtjs', label: 'NuxtUI' },
  { icon: 'i-devicon:pandas', label: 'Pandas' },
  { icon: 'i-devicon:powershell', label: 'PowerShell' },
  { icon: 'i-devicon:postgresql', label: 'PostgreSQL' },
  { icon: 'i-devicon:primeng', label: 'PrimeNG' },
  { icon: 'i-devicon:python', label: 'Python' },
  { icon: 'i-devicon:ruby', label: 'Ruby' },
  { icon: 'i-devicon:sqldeveloper', label: 'PL/SQL' },
  { icon: 'i-devicon:swagger', label: 'Swagger' },
  { icon: 'i-devicon:tailwindcss', label: 'TailwindCSS' },
  { icon: 'i-devicon:typescript', label: 'TypeScript' },
  { icon: 'i-devicon:vitejs', label: 'Vite' },
  { icon: 'i-devicon:vuejs', label: 'Vue.js' },
  { icon: 'i-devicon:vscode', label: 'VS Code' },
  { icon: 'i-devicon:wordpress', label: 'WordPress' },
  { icon: 'i-lucide-squircle-dashed', label: '...und es werden mehr!' },
]
</script>
