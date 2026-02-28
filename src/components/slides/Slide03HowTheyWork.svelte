<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Bajo el capó</span>
      <h2 class="title">¿Cómo funcionan<br />por dentro?</h2>
    </div>

    <div class="main-layout">
      <!-- Loop diagram -->
      <div class="loop-diagram card-glass">
        <h3 class="loop-title">El bucle del agente</h3>
        <div class="loop-steps">
          <div class="step">
            <div class="step-number">1</div>
            <div class="step-body">
              <span class="step-name">Leer</span>
              <span class="step-desc">Tu instrucción + contexto del proyecto</span>
            </div>
          </div>
          <div class="step-arrow">↓</div>
          <div class="step">
            <div class="step-number">2</div>
            <div class="step-body">
              <span class="step-name">Razonar</span>
              <span class="step-desc">¿Qué herramientas necesito para esto?</span>
            </div>
          </div>
          <div class="step-arrow">↓</div>
          <div class="step">
            <div class="step-number">3</div>
            <div class="step-body">
              <span class="step-name">Actuar</span>
              <span class="step-desc">Llama a tools: leer archivo, buscar, editar…</span>
            </div>
          </div>
          <div class="step-arrow">↓</div>
          <div class="step">
            <div class="step-number">4</div>
            <div class="step-body">
              <span class="step-name">Observar</span>
              <span class="step-desc">Recibe el resultado de la tool call</span>
            </div>
          </div>
          <div class="step-arrow loop-back">↺ vuelve al 2 si necesita más pasos</div>
        </div>
      </div>

      <!-- Right column: key concepts -->
      <div class="concepts">
        <div class="concept-card card-glass">
          <div class="concept-icon">🧠</div>
          <div class="concept-body">
            <h4>Context Window</h4>
            <p>Es la memoria de trabajo del agente. Todo lo que "ve": tu instrucción, el código, el historial, los resultados de tools. <strong>Finita y preciosa.</strong></p>
          </div>
        </div>

        <div class="concept-card card-glass">
          <div class="concept-icon">🔧</div>
          <div class="concept-body">
            <h4>Tool Calling</h4>
            <p>El agente puede llamar funciones reales: leer archivos, ejecutar comandos, buscar en la web, llamar a APIs. No solo genera texto.</p>
          </div>
        </div>

        <div class="concept-card card-glass">
          <div class="concept-icon">📋</div>
          <div class="concept-body">
            <h4>System Prompt</h4>
            <p>Las instrucciones permanentes que definen quién es el agente, qué puede hacer y cómo debe comportarse. La base de todo.</p>
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
      radial-gradient(ellipse at 70% 30%, rgba(59, 130, 246, 0.08) 0%, transparent 55%),
      radial-gradient(ellipse at 20% 70%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
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
    overflow-y: auto;
    max-height: 100vh;
    -webkit-overflow-scrolling: touch;
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
    margin-bottom: 0;
    line-height: 1.15;
  }

  /* Main layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.4fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  /* Loop diagram */
  .loop-diagram {
    padding: var(--spacing-xl);
  }

  .loop-title {
    font-family: var(--font-mono);
    font-size: 0.85rem;
    font-weight: 600;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    margin-bottom: var(--spacing-lg);
  }

  .loop-steps {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .step {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    background: rgba(59, 130, 246, 0.06);
    border: 1px solid rgba(96, 165, 250, 0.12);
    border-radius: var(--radius-sm);
    padding: var(--spacing-md) var(--spacing-lg);
  }

  .step-number {
    width: 32px;
    height: 32px;
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-mono);
    font-weight: 800;
    font-size: 0.9rem;
    color: var(--color-base-dark);
    flex-shrink: 0;
  }

  .step-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .step-name {
    font-family: var(--font-display);
    font-weight: 700;
    font-size: 1rem;
    color: var(--color-neutral-light);
  }

  .step-desc {
    font-size: 0.8rem;
    color: var(--color-neutral-light);
    opacity: 0.6;
    font-family: var(--font-body);
  }

  .step-arrow {
    text-align: center;
    color: var(--color-electric);
    opacity: 0.5;
    font-size: 1.2rem;
    line-height: 1;
  }

  .loop-back {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.7;
    background: rgba(59, 130, 246, 0.08);
    border: 1px dashed rgba(96, 165, 250, 0.3);
    border-radius: var(--radius-sm);
    padding: var(--spacing-sm) var(--spacing-md);
    text-align: center;
  }

  /* Concepts */
  .concepts {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .concept-card {
    display: flex;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
    align-items: flex-start;
  }

  .concept-icon {
    font-size: 2rem;
    line-height: 1;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .concept-body h4 {
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin-bottom: var(--spacing-xs);
  }

  .concept-body p {
    font-size: 0.88rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .concept-body strong {
    color: var(--color-electric);
    opacity: 1;
    font-weight: 700;
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
    }

    .title {
      font-size: clamp(1.6rem, 5vw, 2.4rem);
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .loop-diagram {
      padding: var(--spacing-lg);
    }

    .loop-title {
      font-size: 0.8rem;
      margin-bottom: var(--spacing-md);
    }

    .step {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
      min-height: 44px;
    }

    .step-number {
      width: 28px;
      height: 28px;
      font-size: 0.85rem;
    }

    .step-name {
      font-size: 0.95rem;
    }

    .step-desc {
      font-size: 0.75rem;
    }

    .step-arrow {
      font-size: 1rem;
    }

    .loop-back {
      font-size: 0.68rem;
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .concepts {
      gap: var(--spacing-sm);
    }

    .concept-card {
      padding: var(--spacing-md) var(--spacing-lg);
      gap: var(--spacing-md);
      min-height: 44px;
    }

    .concept-icon {
      font-size: 1.6rem;
    }

    .concept-body h4 {
      font-size: 1rem;
    }

    .concept-body p {
      font-size: 0.82rem;
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

    .loop-diagram {
      padding: var(--spacing-md);
    }

    .loop-title {
      font-size: 0.75rem;
      margin-bottom: var(--spacing-sm);
    }

    .loop-steps {
      gap: 2px;
    }

    .step {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
      min-height: 48px;
    }

    .step-number {
      width: 24px;
      height: 24px;
      font-size: 0.8rem;
    }

    .step-name {
      font-size: 0.9rem;
    }

    .step-desc {
      font-size: 0.7rem;
    }

    .step-arrow {
      font-size: 0.9rem;
    }

    .loop-back {
      font-size: 0.62rem;
      padding: var(--spacing-xs) var(--spacing-sm);
    }

    .concept-card {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .concept-icon {
      font-size: 1.4rem;
    }

    .concept-body h4 {
      font-size: 0.9rem;
      margin-bottom: 2px;
    }

    .concept-body p {
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

    .loop-diagram {
      padding: var(--spacing-sm);
    }

    .loop-title {
      font-size: 0.7rem;
    }

    .step {
      padding: var(--spacing-sm);
      min-height: 44px;
    }

    .step-number {
      width: 22px;
      height: 22px;
      font-size: 0.75rem;
    }

    .step-name {
      font-size: 0.85rem;
    }

    .step-desc {
      font-size: 0.65rem;
    }

    .step-arrow {
      font-size: 0.8rem;
    }

    .loop-back {
      font-size: 0.58rem;
    }

    .concept-card {
      padding: var(--spacing-sm);
    }

    .concept-icon {
      font-size: 1.2rem;
    }

    .concept-body h4 {
      font-size: 0.85rem;
    }

    .concept-body p {
      font-size: 0.7rem;
    }
  }
</style>
