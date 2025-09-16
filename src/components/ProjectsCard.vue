<template>
  <UCard variant="subtle">
    <template #header> <div class="text-xl font-bold">Projekte</div></template>
    <div class="flex flex-col gap-5">
      <ProjectComponent
        title="TrackYourThings"
        ongoing
        description="Ein persönliches Projekt, bei dem mithilfe einer Web-App verschiedene Dinge getrackt werden können."
        :used-technologies="['C#', 'PostgreSQL', 'Vue.js', 'TailwindCSS', 'TypeScript']"
        github-link="https://github.com/elsinan/TrackYourThings"
        project-link="http://trackyourthings-frontend.polandcentral.azurecontainer.io/"
      />
      <ProjectComponent
        :image-srcs="[
          './src/assets/consent_server_admin.png',
          './src/assets/consent_server_user.png',
        ]"
        title="ConsentServer"
        ongoing
        description="Masterprojekt und -arbeit zum Thema Consent Management in den Bildungswissenschaften an der HTWK. Für Anwendungen, bei denen personenbezogene Daten verarbeitet werden müssen und nicht zwingend notwendig für das Studienerfolg sind, muss eine Einwilligung eingeholt werden. Der Consent Server zentralisiert die Einholung sowie Verwaltung der Einwilligungen und Datenschutzerklärungen für die Anwendungen."
        :used-technologies="['C#', 'PostgreSQL', 'Vue.js', 'TailwindCSS', 'TypeScript']"
        github-link="https://gitlab.dit.htwk-leipzig.de/masterprojekt-consent-server-2024"
        project-link="https://gitlab.dit.htwk-leipzig.de/masterprojekt-consent-server-2024"
      />
    </div>
  </UCard>
</template>

<script setup lang="ts"></script>
