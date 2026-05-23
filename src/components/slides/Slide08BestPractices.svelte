<script lang="ts">
  import SlideCompare from '@codigosinsiesta/theme/slides/SlideCompare.svelte';
</script>

<SlideCompare
  eyebrow="Buenas prácticas"
  title="Cómo trabajar con agentes"
  titleHighlight="trabajar"
  leftKind="err"
  rightKind="ok"
  left={{
    label: 'No hagas esto',
    headline: 'Recetas para el desastre',
    items: [
      'Confiar ciegamente en código sin tests',
      'Dar tareas enormes en un solo prompt',
      'Pedir decisiones de arquitectura sin contexto',
      'Ignorar el código generado sin leerlo',
      'Usar el agente como oráculo de hechos',
      'No versionar el CLAUDE.md / AGENTS.md'
    ]
  }}
  right={{
    label: 'Haz esto',
    headline: 'El flujo que funciona',
    items: [
      'Revisa SIEMPRE el código — tú eres el responsable',
      'Dale contexto de arquitectura antes de pedir código',
      'Usa CLAUDE.md para codificar las reglas del proyecto',
      'Tareas pequeñas y focalizadas, itera en conversaciones cortas',
      'Lee el código del PR, no solo el plan',
      'Usa el agente para boilerplate, tests y documentación'
    ]
  }}
/>
