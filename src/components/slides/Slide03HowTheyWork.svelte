<script lang="ts">
  import SlideDidactic from '@codigosinsiesta/theme/slides/SlideDidactic.svelte';
</script>

<SlideDidactic
  eyebrow="Bajo el capó"
  title="¿Cómo funcionan por dentro?"
  titleHighlight="funcionan"
  definition={{
    title: '¿Qué es un agente?',
    body: 'Un **LLM con acceso a herramientas** (tools). En cada turno: recibe contexto → razona → decide qué tool llamar → observa el resultado → itera hasta completar la tarea.'
  }}
  analogy={{
    title: 'El bucle del agente',
    body: '`Observe → Think → Act → Observe…` Igual que un junior: lee el código, decide qué cambiar, aplica el cambio, ve si compiló, repite. Sin el bucle, es solo un chatbot.'
  }}
  examples={{
    title: 'Tools típicas',
    items: [
      'read_file / write_file — leer y editar ficheros del repo',
      'run_command — ejecutar tests, builds, scripts',
      'web_search — buscar documentación actualizada',
      'mcp_tool — cualquier servidor MCP conectado'
    ]
  }}
/>
