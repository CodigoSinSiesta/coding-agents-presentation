<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const contextFiles = [
    {
      file: 'CLAUDE.md',
      tool: 'Claude Code',
      color: '#3B82F6',
      content: 'Arquitectura del proyecto, reglas de estilo, comandos de build y test, contexto del dominio.',
    },
    {
      file: '.cursorrules',
      tool: 'Cursor',
      color: '#0ea5e9',
      content: 'Instrucciones de código, frameworks a usar, patrones prohibidos, convenciones del equipo.',
    },
    {
      file: 'copilot-instructions.md',
      tool: 'GitHub Copilot',
      color: '#6d28d9',
      content: 'En .github/. Personaliza el comportamiento de Copilot Chat para tu repositorio.',
    },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El arte de la información</span>
      <h2 class="title">Gestión de <span class="highlight">contexto</span></h2>
      <p class="subtitle">Lo que el agente no sabe, lo inventa.</p>
    </div>

    <div class="main-layout">
      <!-- Left: what is context -->
      <div class="left-col">
        <div class="what-card card-glass">
          <h3>¿Qué hay en el contexto?</h3>
          <div class="context-layers">
            <div class="layer" style="--layer-color: rgba(59, 130, 246, 0.3)">
              <span class="layer-icon">📋</span>
              <span class="layer-name">System Prompt</span>
              <span class="layer-size">~2k tokens</span>
            </div>
            <div class="layer" style="--layer-color: rgba(96, 165, 250, 0.2)">
              <span class="layer-icon">💬</span>
              <span class="layer-name">Historial de conversación</span>
              <span class="layer-size">variable</span>
            </div>
            <div class="layer" style="--layer-color: rgba(30, 58, 138, 0.3)">
              <span class="layer-icon">📁</span>
              <span class="layer-name">Archivos leídos (tool calls)</span>
              <span class="layer-size">~grandes</span>
            </div>
            <div class="layer" style="--layer-color: rgba(30, 58, 138, 0.15)">
              <span class="layer-icon">🔧</span>
              <span class="layer-name">Resultados de herramientas</span>
              <span class="layer-size">variable</span>
            </div>
            <div class="layer limit-layer">
              <span class="layer-icon">🚫</span>
              <span class="layer-name">Límite de contexto</span>
              <span class="layer-size danger">200k tokens</span>
            </div>
          </div>
        </div>

        <div class="tip-card">
          <span class="tip-icon">💡</span>
          <p>Cuanto más largo el contexto, más <strong>cara</strong> la petición y más probabilidad de que el modelo "olvide" lo que dijiste al principio. Mantén el foco.</p>
        </div>
      </div>

      <!-- Right: context files per tool -->
      <div class="right-col">
        <h3 class="files-title">Archivos de contexto por herramienta</h3>
        {#each contextFiles as cf}
          <div class="context-file-card card-glass">
            <div class="cf-header">
              <code class="cf-filename" style="color: {cf.color}">{cf.file}</code>
              <span class="cf-tool" style="background: {cf.color}20; border-color: {cf.color}40; color: {cf.color}">{cf.tool}</span>
            </div>
            <p class="cf-content">{cf.content}</p>
          </div>
        {/each}

        <div class="pro-tip card-glass">
          <span class="pro-icon">⚡</span>
          <div class="pro-body">
            <span class="pro-title">Pro tip</span>
            <p>Empieza siempre con un <code>CLAUDE.md</code> o <code>.cursorrules</code> básico. Documenta ahí la arquitectura, los patrones que usas y los que NUNCA debes usar. El agente lo leerá en cada conversación.</p>
          </div>
        </div>
      </div>
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
      radial-gradient(ellipse at 80% 15%, rgba(59, 130, 246, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 20% 85%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
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
    color: var(--color-electric);
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
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .subtitle {
    font-size: 1rem;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: 0;
    font-family: var(--font-mono);
  }

  /* Layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  .left-col, .right-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  /* What card */
  .what-card {
    padding: var(--spacing-xl);
  }

  .what-card h3 {
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-electric);
    margin-bottom: var(--spacing-lg);
  }

  .context-layers {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .layer {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    padding: var(--spacing-sm) var(--spacing-md);
    background: var(--layer-color, rgba(30, 58, 138, 0.15));
    border-radius: var(--radius-sm);
    border: 1px solid rgba(96, 165, 250, 0.1);
  }

  .limit-layer {
    background: rgba(239, 68, 68, 0.08) !important;
    border-color: rgba(239, 68, 68, 0.2) !important;
    margin-top: var(--spacing-xs);
    border-style: dashed !important;
  }

  .layer-icon { font-size: 1rem; flex-shrink: 0; }

  .layer-name {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    flex: 1;
  }

  .layer-size {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.7;
    white-space: nowrap;
  }

  .layer-size.danger {
    color: #f87171;
    opacity: 1;
    font-weight: 700;
  }

  /* Tip card */
  .tip-card {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(255, 189, 46, 0.05);
    border: 1px solid rgba(255, 189, 46, 0.2);
    border-radius: var(--radius-sm);
  }

  .tip-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 2px; }

  .tip-card p {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .tip-card strong { color: #ffbd2e; font-weight: 700; }

  /* Context files */
  .files-title {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.7;
    margin-bottom: 0;
  }

  .context-file-card {
    padding: var(--spacing-lg);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .cf-header {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: var(--spacing-md);
  }

  .cf-filename {
    font-family: var(--font-mono);
    font-size: 0.9rem;
    font-weight: 700;
  }

  .cf-tool {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    font-weight: 700;
    padding: 2px 8px;
    border-radius: 999px;
    border: 1px solid;
    white-space: nowrap;
    letter-spacing: 0.05em;
  }

  .cf-content {
    font-size: 0.8rem;
    color: var(--color-neutral-light);
    opacity: 0.7;
    line-height: 1.55;
    margin-bottom: 0;
  }

  /* Pro tip */
  .pro-tip {
    display: flex;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg);
    border-color: rgba(59, 130, 246, 0.35);
    background: rgba(59, 130, 246, 0.1);
  }

  .pro-icon { font-size: 1.5rem; flex-shrink: 0; margin-top: 2px; }

  .pro-body { display: flex; flex-direction: column; gap: var(--spacing-xs); }

  .pro-title {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    color: var(--color-electric);
    font-weight: 700;
  }

  .pro-body p {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .pro-body code {
    font-family: var(--font-mono);
    color: var(--color-electric);
    background: rgba(96, 165, 250, 0.1);
    padding: 1px 4px;
    border-radius: 3px;
  }

  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
  }
</style>
