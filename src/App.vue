<script setup lang="ts">
import HomePage from './views/HomePage.vue'
</script>

<template>
  <UApp>
    <div class="flex flex-col">
      <PageHeader />
      <div class="my-5" ref="contentContainer">
        <HomePage />
      </div>
    </div>
  </UApp>
</template>
