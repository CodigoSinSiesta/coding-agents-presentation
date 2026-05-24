<script lang="ts">
  import SlideCompare from '@codigosinsiesta/theme/slides/SlideCompare.svelte';
</script>

<SlideCompare
  eyebrow="Craftmanship"
  title="Buenas prácticas"
  titleHighlight="prácticas"
  subtitle="El agente es tan bueno como el desarrollador que lo dirige."
  leftKind="err"
  rightKind="ok"
  left={{
    label: 'Evita esto',
    items: [
      'No confíes ciegamente en código sin tests',
      'No des tareas enormes en un solo prompt',
      'No le pidas que tome decisiones de arquitectura sin contexto',
      'No copies APIs o paquetes que el agente "inventa"',
      'No uses el agente como sustituto de entender el problema',
      'No dejes sesiones largas sin resetear el contexto',
      'No apruebes planes a ciegas: aprobar = delegar 100% al agente'
    ]
  }}
  right={{
    label: 'Hazlo',
    items: [
      'Usa el agente para tareas repetitivas: boilerplate, tests, documentación',
      'Dale contexto de arquitectura. El agente no adivina tu estilo',
      'Revisa SIEMPRE el código generado. Tú eres el responsable',
      'Haz preguntas de alto nivel, deja los detalles al agente',
      'Usa `CLAUDE.md` / `AGENTS.md` para codificar las reglas del proyecto',
      'Itera en conversaciones cortas y enfocadas',
      'Lee el código del PR, no solo el plan: **1.000 líneas de plan ≈ 1.000 líneas de código**'
    ]
  }}
  insight={{
    icon: '🤖',
    body: 'El agente es **Jarvis**. Tú eres **Tony Stark**. Jarvis no construye el traje solo. Tú diriges, él ejecuta. Invierte el rol y el resultado será una catástrofe.'
  }}
/>
