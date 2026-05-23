<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="El siguiente nivel"
  title="Harness Engineering"
  titleHighlight="Harness Engineering"
  columns={2}
  items={[
    {
      title: 'Code is free',
      body: 'Producir, refactorizar y borrar código **deja de ser escaso**. Cada engineer tiene 5–50–5.000 colaboradores 24/7. La migración de 6 meses se cierra lanzando 15 agentes.'
    },
    {
      title: 'El recurso escaso: atención',
      body: 'El cuello de botella ya no es teclear. Es la **atención humana**, la del modelo y el context window. Hay que estructurar el repo para gastarlos bien.'
    },
    {
      title: 'El repo es prompt persistente',
      body: 'Cada fichero que el agente lee es parte de su **prompt implícito**. Nombres claros, estructura semántica, buena documentación = agentes más precisos.'
    },
    {
      title: 'De vibe coding a ingeniería',
      body: 'No es solo usar la IA más rápido. Es **diseñar sistemas** en los que los agentes operen de forma predecible. NLAH + Meta-Harness (Stanford/Tsinghua, 2026).'
    }
  ]}
/>
