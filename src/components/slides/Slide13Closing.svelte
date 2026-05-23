<script lang="ts">
  import SlideResources from '@codigosinsiesta/theme/slides/SlideResources.svelte';
</script>

<SlideResources
  eyebrow="Cierre"
  title="Lo que te llevas hoy"
  titleHighlight="llevas"
  closing="Hecho con ♥ por Código Sin Siesta · 2025"
  takeaways={[
    { text: 'El agente es **Jarvis**, tú eres **Tony Stark**. Dirige, no abdiques.' },
    { text: 'Sin **System Prompt sólido**, sin resultados predecibles.' },
    { text: '**Contexto es poder** — `CLAUDE.md` / `AGENTS.md` son tu mejor inversión.' },
    { text: 'Revisa siempre: el código **no es tuyo hasta que lo entiendes**.' },
    { text: 'Las **alucinaciones se previenen**, no se aceptan.' },
    { text: '**Harness engineering**: estructura el repo como prompt persistente.' }
  ]}
  links={[
    {
      icon: '🚀',
      title: 'Más presentaciones',
      url: 'https://codigosinsiesta.github.io',
      tag: 'web'
    },
    {
      icon: '📖',
      title: 'The 12-Factor Agents',
      url: 'https://github.com/humanlayer/12-factor-agents',
      tag: 'github'
    }
  ]}
  qr={{ title: 'Código Sin Siesta', url: 'https://codigosinsiesta.github.io' }}
/>
