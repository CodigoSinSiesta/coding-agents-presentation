<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const techniques = [
    {
      icon: '📄',
      title: 'Contexto explícito',
      desc: 'Da al agente la información que necesita. No asumas que "sabe" tu proyecto.',
      example: 'Incluye package.json, estructura de carpetas, versiones exactas.',
      color: '#3B82F6',
    },
    {
      icon: '🎯',
      title: 'Instrucciones específicas',
      desc: 'Sé preciso en el System Prompt. Ambigüedad = alucinaciones.',
      example: '"Usa React 19 con TypeScript strict. Sin any. Sin as."',
      color: '#10b981',
    },
    {
      icon: '🔍',
      title: 'Pide verificación',
      desc: 'Instrucción explícita: "Si no estás seguro de algo, pregunta antes de inventar."',
      example: 'En el system prompt: NEVER guess. Ask when uncertain.',
      color: '#f59e0b',
    },
    {
      icon: '✅',
      title: 'Revisa y verifica',
      desc: 'El código generado no es tu código hasta que lo entiendes y compruebas.',
      example: 'Corre los tests, lee lo que generó, no solo copiar-pegar ciegamente.',
      color: '#8b5cf6',
    },
    {
      icon: '🔄',
      title: 'Contexto fresco',
      desc: 'Las conversaciones largas degradan la calidad. Restablece el contexto.',
      example: 'Empieza nuevas sesiones para tareas distintas. Mantén el foco.',
      color: '#ec4899',
    },
    {
      icon: '📋',
      title: 'CLAUDE.md / .cursorrules',
      desc: 'Archivos de contexto permanente del proyecto que el agente lee automáticamente.',
      example: 'Define arquitectura, convenciones, dependencias y reglas del proyecto.',
      color: '#60A5FA',
    },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Control y prevención</span>
      <h2 class="title">Cómo <span class="highlight">evitar</span> las alucinaciones</h2>
      <p class="subtitle">No es suerte. Es técnica y disciplina.</p>
    </div>

    <div class="techniques-grid">
      {#each techniques as tech}
        <div class="tech-card card-glass">
          <div class="tech-header">
            <span class="tech-icon">{tech.icon}</span>
            <h3 class="tech-title" style="color: {tech.color}">{tech.title}</h3>
          </div>
          <p class="tech-desc">{tech.desc}</p>
          <div class="tech-example">
            <span class="example-label">Ejemplo:</span>
            <span class="example-text">{tech.example}</span>
          </div>
        </div>
      {/each}
    </div>
  </div>
</div>

<style>
  .swiper-slide {
    position: relative;
    width: 100%;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    overflow: hidden;
  }

  .slide-background {
    position: absolute;
    inset: 0;
    background:
      radial-gradient(ellipse at 20% 20%, rgba(16, 185, 129, 0.06) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 80%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
    z-index: 1;
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 1200px;
    width: 100%;
    padding: var(--spacing-xl) var(--spacing-content);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-xl);
  }

  .slide-header { text-align: center; }

  .label {
    display: inline-block;
    font-family: var(--font-mono);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    color: #34d399;
    margin-bottom: var(--spacing-sm);
  }

  .title {
    font-size: clamp(2rem, 4.5vw, 3.2rem);
    font-weight: 800;
    color: var(--color-neutral-light);
    margin-bottom: var(--spacing-sm);
    line-height: 1.15;
  }

  .highlight {
    background: linear-gradient(135deg, #10b981, #34d399);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .subtitle {
    font-size: 1rem;
    color: #34d399;
    opacity: 0.8;
    margin-bottom: 0;
    font-family: var(--font-mono);
  }

  /* Techniques grid */
  .techniques-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-lg);
  }

  .tech-card {
    padding: var(--spacing-xl);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    transition: all var(--transition-base);
  }

  .tech-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
  }

  .tech-icon {
    font-size: 1.6rem;
    line-height: 1;
    flex-shrink: 0;
  }

  .tech-title {
    font-size: 1.05rem;
    font-weight: 700;
    margin-bottom: 0;
    font-family: var(--font-display);
  }

  .tech-desc {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
    flex: 1;
  }

  .tech-example {
    display: flex;
    flex-direction: column;
    gap: 4px;
    padding: var(--spacing-sm) var(--spacing-md);
    background: rgba(10, 22, 40, 0.4);
    border-radius: var(--radius-sm);
    border-left: 2px solid rgba(96, 165, 250, 0.3);
  }

  .example-label {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--color-electric);
    opacity: 0.6;
  }

  .example-text {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    color: var(--color-neutral-light);
    opacity: 0.7;
    line-height: 1.5;
  }

  @media (max-width: 1024px) {
    .techniques-grid { grid-template-columns: repeat(2, 1fr); }
  }

  @media (max-width: 600px) {
    .techniques-grid { grid-template-columns: 1fr; }
  }
</style>
