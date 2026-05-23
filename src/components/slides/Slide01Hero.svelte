<script lang="ts">
  import SlideHero from '@codigosinsiesta/theme/slides/SlideHero.svelte';
</script>

<SlideHero
  eyebrow="Código Sin Siesta · 2025"
  title="Tu nuevo compañero de codificación"
  titleHighlight="compañero"
  subtitle="Agentes de IA: cómo trabajar con ellos sin perder el control"
  tools={[
    { label: 'Claude Code' },
    { label: 'GitHub Copilot' },
    { label: 'Cursor' },
    { label: 'Codex' },
    { label: 'Gemini CLI', highlight: true },
  ]}
  author={{
    name: 'Alejandro de la Fuente',
    role: 'Technical Leader Specialist · Código Sin Siesta',
    links: [{ url: 'https://codigosinsiesta.github.io', label: 'codigosinsiesta.github.io' }]
  }}
/>
