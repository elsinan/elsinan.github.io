<template>
  <UCard variant="subtle">
    <template #header> <div class="text-xl font-bold">Projekte</div></template>
    <div class="flex flex-col gap-5">
      <ProjectComponent
        title="TrackYourThings"
        ongoing
        description="Ein persönliches Projekt, bei dem mithilfe einer Web-App verschiedene Dinge getrackt werden können. Die Anmeldung erfolgt über Passekeys (Webauthn)."
        :used-technologies="['C#', 'PostgreSQL', 'Vue.js', 'TailwindCSS', 'TypeScript']"
        github-link="https://github.com/elsinan/TrackYourThings"
        project-link="https://track-your-things.vercel.app/"
      />
      <ProjectComponent
        title="Leipzig Lakers Webseite"
        ongoing
        :images="[
          { src: 'leipzig_lakers_new.png', scale: '100' },
          { src: 'leipzig_lakers_old.png', scale: '100' },
        ]"
        description="Umbau des Internetauftritts des Basketballvereins Leipzig Lakers und grafisches Update zu einer modernen Oberfläche."
        :used-technologies="['WordPress']"
        project-link="https://www.leipziglakers.de/"
      />
      <ProjectComponent
        :images="[
          { src: 'consent_server_admin.png', scale: '100' },
          { src: 'consent_server_user.png', scale: '70' },
        ]"
        title="ConsentServer"
        description="Masterprojekt und -arbeit zum Thema Consent Management in den Bildungswissenschaften an der HTWK: Für Anwendungen, bei denen personenbezogene Daten verarbeitet werden müssen und die nicht zwingend notwendig für den Studienerfolg sind, muss eine Einwilligung eingeholt werden. Der ConsentServer zentralisiert die Einholung sowie Verwaltung der Einwilligungen und Datenschutzerklärungen für die Anwendungen."
        :used-technologies="['C#', 'PostgreSQL', 'Vue.js', 'TailwindCSS', 'TypeScript']"
        github-link="https://gitlab.dit.htwk-leipzig.de/consent-server"
        project-link="https://gitlab.dit.htwk-leipzig.de/consent-server"
      />
    </div>
  </UCard>
</template>

<script setup lang="ts"></script>
