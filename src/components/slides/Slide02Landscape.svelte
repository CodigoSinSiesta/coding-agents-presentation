<script lang="ts">
  import SlideToolsGrid from '@codigosinsiesta/theme/slides/SlideToolsGrid.svelte';
</script>

<SlideToolsGrid
  eyebrow="El ecosistema"
  title="El panorama actual"
  titleHighlight="panorama"
  intro="En 2025 los agentes de codificación son herramientas de producción. Conocer su fortaleza marca la diferencia."
  columns={3}
  tools={[
    {
      icon: '🐙',
      title: 'GitHub Copilot',
      subtitle: 'IDE Plugin',
      tag: 'Microsoft',
      body: 'El pionero. Autocompletado + chat. Integrado en VS Code y JetBrains.',
      meta: ['Completions', 'Chat', 'PR summaries']
    },
    {
      icon: '⚡',
      title: 'Cursor',
      subtitle: 'IDE propio',
      tag: 'Cursor AI',
      body: 'Fork de VS Code con agente nativo. Composer para cambios multi-archivo.',
      meta: ['Multi-file', 'Composer', 'Context-aware']
    },
    {
      icon: '🤖',
      title: 'Claude Code',
      subtitle: 'CLI + agente',
      tag: 'Anthropic',
      accent: '#3B82F6',
      body: 'Agente de terminal con contexto de repo completo. Skills y subagentes.',
      meta: ['Terminal', 'Skills', 'Subagents']
    },
    {
      icon: '🌊',
      title: 'Codex / ChatGPT',
      subtitle: 'Web + API',
      tag: 'OpenAI',
      body: 'Modelos potentes. Canvas para edición colaborativa de código.',
      meta: ['Canvas', 'API', 'o3']
    },
    {
      icon: '💎',
      title: 'Gemini CLI',
      subtitle: 'CLI',
      tag: 'Google',
      body: 'Ventana de 2M tokens. Integración nativa con el ecosistema Google.',
      meta: ['2M context', 'Grounding', 'Free tier']
    },
    {
      icon: '🧩',
      title: 'Windsurf / Cline',
      subtitle: 'IDE / extensión',
      tag: 'Open source',
      body: 'Alternativas open-source con soporte multi-modelo y MCP nativo.',
      meta: ['Multi-model', 'MCP', 'Open source']
    }
  ]}
/>
