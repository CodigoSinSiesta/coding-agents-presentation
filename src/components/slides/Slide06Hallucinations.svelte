<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const examples = [
    {
      icon: '📦',
      title: 'Paquetes que no existen',
      real: 'import { superTool } from "nonexistent-lib"',
      problem: 'El agente inventa una API que nunca existió',
    },
    {
      icon: '📋',
      title: 'APIs incorrectas',
      real: 'react.useState(0)',
      problem: 'Mezcla sintaxis de versiones distintas o APIs deprecadas',
    },
    {
      icon: '📁',
      title: 'Archivos que no existen',
      real: 'import config from "./config/db.ts"',
      problem: 'El agente asume una estructura de proyecto que no es la real',
    },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El enemigo número uno</span>
      <h2 class="title">¿Qué son las <span class="highlight">alucinaciones</span>?</h2>
    </div>

    <div class="main-layout">
      <!-- Left: definition -->
      <div class="left-col">
        <div class="definition card-glass">
          <div class="def-header">
            <span class="def-icon">🧠</span>
            <h3>Definición técnica</h3>
          </div>
          <p>Un LLM genera texto estadísticamente probable basado en su entrenamiento. Cuando no tiene información suficiente, <strong>inventa respuestas que suenan correctas pero son falsas</strong>. No sabe que está mintiendo.</p>
        </div>

        <div class="analogy card-glass">
          <div class="ana-header">
            <span class="ana-icon">🏗️</span>
            <span class="ana-label">Analogía</span>
          </div>
          <p>Es como un arquitecto que, cuando no conoce una normativa concreta, <strong>inventa una normativa plausible</strong> en lugar de decir "no lo sé". El edificio parece bien diseñado hasta que aparece el inspector.</p>
        </div>

        <div class="stats-row">
          <div class="stat card-glass">
            <span class="stat-value">~30%</span>
            <span class="stat-label">de errores en código generado son alucinaciones</span>
          </div>
          <div class="stat card-glass">
            <span class="stat-value">↑</span>
            <span class="stat-label">aumentan con tareas largas y sin contexto claro</span>
          </div>
        </div>
      </div>

      <!-- Right: examples -->
      <div class="right-col">
        <h3 class="examples-title">Ejemplos reales en código</h3>
        {#each examples as ex}
          <div class="example-card card-glass">
            <div class="ex-header">
              <span class="ex-icon">{ex.icon}</span>
              <span class="ex-title">{ex.title}</span>
            </div>
            <div class="ex-code-block">
              <span class="ex-code-label">El agente genera:</span>
              <code class="ex-code">{ex.real}</code>
            </div>
            <div class="ex-problem">
              <span class="ex-problem-icon">💥</span>
              <span>{ex.problem}</span>
            </div>
          </div>
        {/each}

        <div class="key-insight">
          <span class="insight-icon">💡</span>
          <p>El modelo no tiene acceso al estado real de tu proyecto. Sin contexto, adivina. Y adivina bien... para las estadísticas. Mal para ti.</p>
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
      radial-gradient(ellipse at 80% 20%, rgba(239, 68, 68, 0.06) 0%, transparent 50%),
      radial-gradient(ellipse at 10% 80%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
    z-index: 1;
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 1200px;
    width: 100%;
    padding: var(--spacing-2xl) var(--spacing-content);
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
    color: #f87171;
    margin-bottom: var(--spacing-sm);
  }

  .title {
    font-size: clamp(2rem, 4.5vw, 3.2rem);
    font-weight: 800;
    color: var(--color-neutral-light);
    margin-bottom: 0;
    line-height: 1.15;
  }

  .highlight {
    background: linear-gradient(135deg, #ef4444, #f97316);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  /* Layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  .left-col, .right-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  /* Definition */
  .definition, .analogy {
    padding: var(--spacing-xl);
  }

  .def-header, .ana-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    margin-bottom: var(--spacing-md);
  }

  .def-icon, .ana-icon { font-size: 1.8rem; }

  .def-header h3 {
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-electric);
    margin-bottom: 0;
  }

  .ana-label {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.7;
  }

  .definition p, .analogy p {
    font-size: 0.88rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.65;
    margin-bottom: 0;
  }

  .definition strong, .analogy strong {
    color: #f87171;
    opacity: 1;
    font-weight: 700;
  }

  /* Stats */
  .stats-row {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-md);
  }

  .stat {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-xs);
    padding: var(--spacing-lg);
    text-align: center;
  }

  .stat-value {
    font-family: var(--font-display);
    font-size: 2rem;
    font-weight: 900;
    color: #f87171;
    line-height: 1;
  }

  .stat-label {
    font-size: 0.75rem;
    color: var(--color-neutral-light);
    opacity: 0.65;
    line-height: 1.4;
    text-align: center;
  }

  /* Examples */
  .examples-title {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.7;
    margin-bottom: 0;
  }

  .example-card {
    padding: var(--spacing-lg);
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .ex-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
  }

  .ex-icon { font-size: 1.2rem; }

  .ex-title {
    font-family: var(--font-display);
    font-size: 0.95rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .ex-code-block {
    display: flex;
    flex-direction: column;
    gap: 4px;
    background: rgba(10, 22, 40, 0.5);
    border-radius: var(--radius-sm);
    padding: var(--spacing-md);
    border-left: 3px solid rgba(239, 68, 68, 0.4);
  }

  .ex-code-label {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    text-transform: uppercase;
    letter-spacing: 0.08em;
    color: var(--color-electric);
    opacity: 0.5;
  }

  .ex-code {
    font-family: var(--font-mono);
    font-size: 0.8rem;
    color: #f87171;
  }

  .ex-problem {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-sm);
    font-size: 0.8rem;
    color: var(--color-neutral-light);
    opacity: 0.7;
    line-height: 1.4;
  }

  .ex-problem-icon { flex-shrink: 0; font-size: 0.9rem; }

  /* Key insight */
  .key-insight {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(59, 130, 246, 0.08);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-sm);
  }

  .insight-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 1px; }

  .key-insight p {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
    font-style: italic;
  }

  /* Mobile: Tablet */
  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
  }

  /* Mobile: Small tablet / large phone */
  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-lg);
      overflow-y: auto;
      max-height: 100vh;
      -webkit-overflow-scrolling: touch;
    }

    .title {
      font-size: clamp(1.6rem, 5vw, 2.4rem);
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .definition, .analogy {
      padding: var(--spacing-lg);
    }

    .def-icon, .ana-icon {
      font-size: 1.5rem;
    }

    .def-header h3 {
      font-size: 0.95rem;
    }

    .stats-row {
      grid-template-columns: 1fr;
      gap: var(--spacing-sm);
    }

    .stat {
      flex-direction: row;
      justify-content: flex-start;
      gap: var(--spacing-md);
      padding: var(--spacing-md);
      text-align: left;
      min-height: 60px;
    }

    .stat-value {
      font-size: 1.6rem;
    }

    .stat-label {
      text-align: left;
      font-size: 0.8rem;
    }

    .examples-title {
      font-size: 0.75rem;
      margin-bottom: var(--spacing-sm);
    }

    .example-card {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .ex-header {
      gap: var(--spacing-sm);
    }

    .ex-icon {
      font-size: 1.1rem;
    }

    .ex-title {
      font-size: 0.9rem;
    }

    .ex-code-block {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .ex-code {
      font-size: 0.75rem;
    }

    .ex-problem {
      font-size: 0.78rem;
    }

    .key-insight {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .key-insight p {
      font-size: 0.8rem;
    }
  }

  /* Mobile: Phone */
  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-md);
    }

    .slide-header {
      margin-bottom: var(--spacing-sm);
    }

    .label {
      font-size: 0.7rem;
      margin-bottom: var(--spacing-xs);
    }

    .title {
      font-size: clamp(1.4rem, 6vw, 1.8rem);
    }

    .definition, .analogy {
      padding: var(--spacing-md);
    }

    .def-header, .ana-header {
      gap: var(--spacing-sm);
      margin-bottom: var(--spacing-sm);
    }

    .def-icon, .ana-icon {
      font-size: 1.3rem;
    }

    .def-header h3 {
      font-size: 0.9rem;
    }

    .definition p, .analogy p {
      font-size: 0.82rem;
      line-height: 1.55;
    }

    .stat {
      padding: var(--spacing-sm) var(--spacing-md);
      min-height: 52px;
    }

    .stat-value {
      font-size: 1.4rem;
    }

    .stat-label {
      font-size: 0.75rem;
    }

    .example-card {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .ex-icon {
      font-size: 1rem;
    }

    .ex-title {
      font-size: 0.85rem;
    }

    .ex-code-block {
      padding: var(--spacing-sm);
    }

    .ex-code-label {
      font-size: 0.6rem;
    }

    .ex-code {
      font-size: 0.7rem;
    }

    .ex-problem {
      font-size: 0.72rem;
      gap: var(--spacing-xs);
    }

    .ex-problem-icon {
      font-size: 0.85rem;
    }

    .key-insight {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .insight-icon {
      font-size: 1rem;
    }

    .key-insight p {
      font-size: 0.75rem;
      line-height: 1.5;
    }
  }

  /* Mobile: Small phone */
  @media (max-width: 390px) {
    .slide-content {
      padding: var(--spacing-sm);
      gap: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.2rem, 6vw, 1.6rem);
    }

    .definition, .analogy {
      padding: var(--spacing-sm);
    }

    .def-header, .ana-header {
      gap: var(--spacing-xs);
      margin-bottom: var(--spacing-xs);
    }

    .def-icon, .ana-icon {
      font-size: 1.2rem;
    }

    .def-header h3 {
      font-size: 0.85rem;
    }

    .definition p, .analogy p {
      font-size: 0.78rem;
    }

    .stat {
      padding: var(--spacing-sm);
      min-height: 48px;
    }

    .stat-value {
      font-size: 1.2rem;
    }

    .stat-label {
      font-size: 0.7rem;
    }

    .example-card {
      padding: var(--spacing-sm);
    }

    .ex-title {
      font-size: 0.8rem;
    }

    .ex-code {
      font-size: 0.65rem;
    }

    .ex-problem {
      font-size: 0.68rem;
    }

    .key-insight {
      padding: var(--spacing-sm);
    }

    .key-insight p {
      font-size: 0.7rem;
    }
  }
</style>
