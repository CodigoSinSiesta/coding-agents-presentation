<script lang="ts">
  import SlidePatternGrid from '@codigosinsiesta/theme/slides/SlidePatternGrid.svelte';
</script>

<SlidePatternGrid
  eyebrow="The 12-Factor Agents"
  title="12 principios para agentes robustos"
  titleHighlight="12 principios"
  intro="Adaptación del **12-factor app** al mundo de los agentes. Cada principio reduce la fragilidad y aumenta la mantenibilidad."
  columns={4}
  patterns={[
    { type: 'custom', svg: '', title: '01 · NL → Tool Calls', body: 'El LLM convierte lenguaje en JSON validable.' },
    { type: 'custom', svg: '', title: '02 · Own your prompts', body: 'Versiona tus prompts como código fuente.' },
    { type: 'custom', svg: '', title: '03 · Own your context', body: 'Tú decides qué entra. La librería no es caja negra.' },
    { type: 'custom', svg: '', title: '04 · Tools = outputs', body: 'La tool call es JSON. La lógica vive en tu código.' },
    { type: 'custom', svg: '', title: '05 · Unify state', body: 'Estado del agente = estado de tu negocio.' },
    { type: 'custom', svg: '', title: '06 · Pause / Resume', body: 'Tu agente se para y reanuda como cualquier proceso.' },
    { type: 'custom', svg: '', title: '07 · Human as tool', body: 'El humano-en-el-loop también es una tool call.' },
    { type: 'custom', svg: '', title: '08 · Own control flow', body: 'Si conoces el workflow, no lo metas en el prompt.' },
    { type: 'custom', svg: '', title: '09 · Compact errors', body: 'Error → mensaje corto accionable, no volcado.' },
    { type: 'custom', svg: '', title: '10 · Small agents', body: 'Mejor varios micro-agentes que un mega-agente.' },
    { type: 'custom', svg: '', title: '11 · Trigger anywhere', body: 'Slack, cron, webhook, email. Donde el usuario vive.' },
    { type: 'custom', svg: '', title: '12 · Stateless reducer', body: 'nuevo_estado = agente(estado, evento). Replay trivial.' },
  ]}
/>
