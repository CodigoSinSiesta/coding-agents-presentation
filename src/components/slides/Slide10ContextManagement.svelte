<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Gestión de contexto"
  title="Cómo alimentar al agente"
  titleHighlight="alimentar"
  columns={2}
  items={[
    {
      title: 'CLAUDE.md',
      body: 'Para **Claude Code**. Arquitectura del proyecto, reglas de estilo, comandos de build y test, contexto del dominio. Se carga automáticamente en cada sesión.'
    },
    {
      title: 'AGENTS.md',
      body: 'Formato **genérico multi-agente**. Compatible con Codex, Gemini CLI, Aider y otros. Describe el proyecto de forma agnóstica al modelo.'
    },
    {
      title: '.cursorrules / .windsurfrules',
      body: 'Equivalentes específicos para **Cursor y Windsurf**. Mismo concepto: contexto persistente que el agente lee antes de cada tarea.'
    },
    {
      title: 'Contexto dinámico',
      body: 'Pasa fragmentos relevantes en el prompt: `package.json`, interfaces TypeScript, esquemas de BD, contratos de API. **El agente no adivina tu arquitectura.**'
    }
  ]}
/>
