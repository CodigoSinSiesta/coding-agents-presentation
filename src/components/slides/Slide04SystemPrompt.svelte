<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="El cerebro del agente"
  title="¿Qué es el System Prompt?"
  titleHighlight="System Prompt"
  columns={2}
  items={[
    {
      title: 'La constitución del agente',
      body: 'Es el **contexto de sistema** que recibe antes de cualquier instrucción tuya. Define personalidad, capacidades, restricciones y herramientas disponibles.'
    },
    {
      title: 'Analogía: el reglamento interno',
      body: 'Como el reglamento de una empresa. El agente lo lee al "incorporarse". Tú puedes extenderlo con `CLAUDE.md` o `AGENTS.md` en tu repo.'
    },
    {
      title: 'Qué contiene',
      body: '**Rol** y propósito del agente · lista de **tools** disponibles · reglas de **seguridad** y límites · **formato** de respuesta esperado · instrucciones de **dominio**.'
    },
    {
      title: 'Por qué importa',
      body: 'Un system prompt mal diseñado → comportamiento impredecible. Un system prompt sólido → resultados consistentes. **Es la diferencia entre un agente útil y uno frustrante.**'
    }
  ]}
/>
