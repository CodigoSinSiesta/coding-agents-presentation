<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="La solución"
  title="Cómo prevenir alucinaciones"
  titleHighlight="prevenir"
  columns={2}
  items={[
    {
      title: 'Contexto explícito',
      body: 'Dale al agente la información que necesita. Incluye `package.json`, estructura de carpetas, versiones exactas. **No asumas que "sabe" tu proyecto.**'
    },
    {
      title: 'Instrucciones específicas',
      body: 'Sé preciso en el system prompt. Ambigüedad = alucinaciones. `"Usa React 19 con TypeScript strict. Sin any. Sin as."` es mejor que `"usa buenas prácticas"`.'
    },
    {
      title: 'Grounding con herramientas',
      body: 'Conecta herramientas de **búsqueda y lectura**. El agente que puede verificar antes de responder alucina mucho menos que el que trabaja solo de memoria.'
    },
    {
      title: 'Tests como red de seguridad',
      body: 'Los tests no previenen alucinaciones, pero **las detectan rápido**. TDD con agentes es poderoso: primero el test, luego el agente implementa hasta que pase.'
    }
  ]}
/>
