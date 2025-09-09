<template>
  <UContainer class="flex flex-col gap-10">
    <IntroductionCard id="introduction" />
    <div class="flex flex-col gap-10 md:flex-row-reverse md:gap-5">
      <TechStack id="techstack" class="flex-3" />
      <TimeLine id="werdegang" class="flex-4" />
    </div>
    <ProjectsCard id="projekte" />
  </UContainer>
</template>

<script setup lang="ts"></script>
