<template>
  <UCard variant="subtle">
    <div class="flex flex-col md:flex-row items-center gap-7">
      <img
        src="@/assets/logo.svg"
        alt="Mein Logo solange noch kein eigenes Bild"
        class="w-50 h-60 bg-accented py-10 px-5 rounded-full overflow-visible"
      />

      <UContainer class="flex flex-col justify-center gap-2">
        <span class="text-xl mb-3">Hallo, ich bin Sinan <span class="text-2xl">👋</span></span>
        <p>Willkommen auf meiner persönlichen GitHub Page!</p>
        <p>
          Ich bin Masterstudent der Informatik aus Leipzig. Neben dem Studium und Werkstudentenjob
          arbeite ich gerne an eigenen Projekten.
        </p>
        <p>
          Und wenn ich nicht gerade programmiere oder studiere, spiele ich in meiner Freizeit
          leidenschaftlich gerne Basketball.
        </p>
        <p>Nutze gerne die Kontaktmöglichkeiten, um mit mir in Verbindung zu treten :)</p>
      </UContainer>
      <UContainer class="flex md:flex-col gap-4 md:w-sm justify-center items-stretch flex-wrap">
        <UButton
          icon="i-devicon:github"
          :variant="isDark ? 'solid' : 'outline'"
          color="neutral"
          label="GitHub"
          href="https://github.com/elsinan"
          class="justify-center items-center flex"
        />

        <UButton
          icon="i-devicon:linkedin"
          :variant="isDark ? 'solid' : 'outline'"
          color="neutral"
          label="LinkedIn"
          href="https://www.linkedin.com/in/sinan-elmas-851bb2383"
          class="justify-center items-center flex"
        />
        <UButton
          leading-icon="i-lucide-mail"
          :variant="isDark ? 'solid' : 'outline'"
          color="neutral"
          label="E-Mail"
          :href="getMailTo(decodedMail)"
          class="justify-center items-center flex"
        />
      </UContainer>
    </div>
  </UCard>
</template>

<script setup lang="ts">
import { ref } from 'vue'
const isDark = ref(window.matchMedia && window.matchMedia('(prefers-color-scheme: dark)').matches)

window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', (event) => {
  if (event.matches) isDark.value = true
  else isDark.value = false
})

const rotate15 = (s: string) => {
  return s.replace(/[A-Za-z]/g, (c) => {
    const base = c <= 'Z' ? 65 : 97
    return String.fromCharCode(((c.charCodeAt(0) - base + 15) % 26) + base)
  })
}

const decodedMail = 'DTYLY.PWXLD@RXI.YPE'.toLowerCase()

const getMailTo = (s: string) => {
  return 'mailto:' + rotate15(s)
}
</script>
