<template>
  <UCard variant="subtle">
    <div class="flex flex-col md:flex-row gap-5">
      <UContainer class="flex flex-col justify-center gap-2">
        <span class="text-xl mb-3">Hallo, ich bin Sinan <span class="text-2xl">👋</span></span>
        <p>Willkommen auf meiner persönlichen GitHubPages-Seite!</p>
        <p>Ich bin Software-Entwickler und Masterstudent der Informatik aus Leipzig.</p>
        <p>Neben dem Programmieren spiele ich in meiner Freizeit leidenschaftlich Basketball.</p>
        <p>Nutze gerne die Kontaktmöglichkeiten, um mit mir in Verbindung zu treten :)</p>
      </UContainer>
      <UContainer class="flex md:flex-col justify-center gap-2 w-min">
        <UButton icon="i-devicon:github" variant="outline" color="neutral" label="GitHub" />

        <UButton icon="i-devicon:linkedin" variant="outline" color="neutral" label="LinkedIn" />
        <UButton
          leading-icon="i-lucide-mail"
          variant="outline"
          color="neutral"
          label="E-Mail"
          :href="getMailTo(decodedMail)"
        />
      </UContainer>
    </div>
  </UCard>
</template>

<script setup lang="ts">
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
