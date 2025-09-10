<template>
  <UContainer class="flex flex-col gap-10">
    <IntroductionCard id="introduction" />
    <div class="flex flex-col gap-10 md:flex-row md:gap-5 md:items-center-safe">
      <TimeLine id="werdegang" class="flex-4" />
      <TechStack id="techstack" class="flex-3" />
    </div>
    <ProjectsCard id="projekte" />
    <PageFooter />
  </UContainer>
</template>

<script setup lang="ts"></script>
