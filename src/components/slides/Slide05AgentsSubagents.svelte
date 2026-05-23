<script lang="ts">
  import SlideList from '@codigosinsiesta/theme/slides/SlideList.svelte';
</script>

<SlideList
  eyebrow="Orquestación"
  title="Agentes y Sub-agentes"
  titleHighlight="Sub-agentes"
  columns={2}
  items={[
    {
      title: 'Orquestador',
      body: 'El agente principal. **Planifica** la tarea, decide qué sub-agentes lanzar y **sintetiza** los resultados. Equivale al tech lead del equipo.'
    },
    {
      title: 'Sub-agentes',
      body: 'Agentes especializados con **contexto reducido** y objetivo único. Uno busca documentación, otro escribe tests, otro revisa seguridad. Trabajan en paralelo.'
    },
    {
      title: '¿Cuándo usarlos?',
      body: 'Cuando la tarea es **demasiado grande** para un solo contexto, cuando hay **partes independientes** que pueden paralelizarse, o cuando necesitas **especialización**.'
    },
    {
      title: 'El riesgo',
      body: 'Más agentes = más complejidad = más puntos de fallo. **Empieza simple**. Un agente monolítico bien diseñado supera a cinco mal coordinados.'
    }
  ]}
/>
