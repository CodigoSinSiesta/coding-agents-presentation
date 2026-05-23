<script lang="ts">
  import SlideHandsOn from '@codigosinsiesta/theme/slides/SlideHandsOn.svelte';
</script>

<SlideHandsOn
  eyebrow="Demo en vivo"
  title="El flujo real con un agente"
  titleHighlight="flujo real"
  intro="Cuatro pasos que convierten una tarea vaga en código de producción. Sin magia, con criterio."
  current={1}
  steps={[
    {
      title: 'CLAUDE.md — contexto del proyecto',
      body: 'Definimos la arquitectura, stack, reglas de estilo y comandos. El agente lo lee antes de empezar.',
      code: '# Mi proyecto\n## Stack: React 19 + TypeScript strict + Vitest\n## Reglas: sin any, sin as, tests obligatorios'
    },
    {
      title: 'Prompt claro con scope definido',
      body: '**Instrucción específica** con criterio de éxito medible. Nada de "mejora el código".',
      code: '$ Crea un hook useForm con validación en tiempo real.\n  Retorna { values, errors, handleChange, handleSubmit }.\n  Tests incluidos. Funciones < 20 líneas.'
    },
    {
      title: 'Agente trabaja — observa el bucle',
      body: 'Lee ficheros → razona → genera código → ejecuta tests → itera. **No interrumpas** hasta que termine o se bloquee.',
      code: '✓ Leyendo src/hooks/...\n✓ Generando useForm.ts\n✓ Generando useForm.test.ts\n✓ Tests: 8 passed'
    },
    {
      title: 'Revisión crítica — tú eres el responsable',
      body: 'Lee el diff completo. Verifica la lógica, no solo que los tests pasen. **El código es tuyo** desde el momento en que lo apruebas.',
    }
  ]}
/>
