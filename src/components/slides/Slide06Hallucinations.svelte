<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="El problema más peligroso"
  title="Alucinaciones en código"
  titleHighlight="Alucinaciones"
  columns={2}
  items={[
    {
      title: 'Paquetes que no existen',
      body: '`import { superTool } from "nonexistent-lib"` — el agente inventa una API que nunca existió. El código compila pero falla en runtime.'
    },
    {
      title: 'APIs incorrectas',
      body: '`react.useState(0)` — mezcla sintaxis de versiones distintas o usa APIs deprecadas. Especialmente grave con librerías de rápida evolución.'
    },
    {
      title: 'Lógica sutilmente errónea',
      body: 'El código parece correcto, los tests pasan, pero el **comportamiento en edge cases es incorrecto**. El peor tipo: falla en producción.'
    },
    {
      title: 'Hechos inventados',
      body: 'El agente inventa datos, referencias o documentación. **"Según la RFC 4512…"** citando algo que no existe. Verificar siempre fuentes externas.'
    }
  ]}
/>
