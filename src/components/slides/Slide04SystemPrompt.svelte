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
      <span class="label">El cerebro del agente</span>
      <h2 class="title">¿Qué es el <span class="highlight">System Prompt</span>?</h2>
      <p class="subtitle">No es magia. Es la constitución del agente.</p>
    </div>

    <div class="main-layout">
      <!-- Left: definition + analogy -->
      <div class="left-col">
        <div class="definition-card card-glass">
          <div class="def-icon">📜</div>
          <div class="def-body">
            <h3>Definición</h3>
            <p>Es un bloque de texto que se pasa al LLM <strong>antes que cualquier mensaje del usuario</strong>. Define la personalidad, las capacidades, las restricciones y el contexto del agente.</p>
          </div>
        </div>

        <div class="analogy-card card-glass">
          <div class="analogy-header">
            <span class="analogy-icon">🏗️</span>
            <span class="analogy-label">Analogía</span>
          </div>
          <p>El System Prompt es como los <strong>planos de un edificio</strong>. No es el edificio en sí, pero define exactamente qué puede ser construido y cómo. Sin planos sólidos, el edificio puede ser cualquier cosa... y eso es peligroso.</p>
        </div>
      </div>

      <!-- Right: code example -->
      <div class="right-col">
        <div class="code-block card-glass">
          <div class="code-header">
            <span class="code-dot red"></span>
            <span class="code-dot yellow"></span>
            <span class="code-dot green"></span>
            <span class="code-filename">system-prompt.md</span>
          </div>
          <pre class="code-content"><code><span class="token-comment"># Quién eres</span>
Eres un agente de codificación experto en
TypeScript y arquitectura limpia.

<span class="token-comment"># Tu misión</span>
Ayudar al desarrollador a escribir código
de producción siguiendo Clean Architecture.

<span class="token-comment"># Tus herramientas disponibles</span>
- read_file: Leer archivos del proyecto
- write_file: Crear o modificar archivos
- run_command: Ejecutar comandos en terminal
- web_search: Buscar documentación

<span class="token-comment"># Restricciones importantes</span>
- NUNCA elimines archivos sin confirmar
- SIEMPRE escribe tests para código nuevo
- Pregunta si no entiendes el contexto</code></pre>
        </div>

        <div class="key-points">
          <div class="key-point">
            <span class="kp-icon">⚡</span>
            <span class="kp-text">El System Prompt consume tokens de contexto <em>en cada petición</em></span>
          </div>
          <div class="key-point">
            <span class="kp-icon">🎯</span>
            <span class="kp-text">Cuanto más específico, menos alucinaciones</span>
          </div>
          <div class="key-point">
            <span class="kp-icon">🔒</span>
            <span class="kp-text">Es la primera línea de defensa contra comportamientos no deseados</span>
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
      radial-gradient(ellipse at 90% 10%, rgba(59, 130, 246, 0.1) 0%, transparent 50%),
      radial-gradient(ellipse at 10% 90%, rgba(30, 58, 138, 0.12) 0%, transparent 50%);
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
    font-size: 1.05rem;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: 0;
    font-family: var(--font-mono);
  }

  /* Layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.3fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  .left-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  .right-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  /* Definition card */
  .definition-card {
    display: flex;
    gap: var(--spacing-lg);
    padding: var(--spacing-xl);
    align-items: flex-start;
  }

  .def-icon {
    font-size: 2.2rem;
    flex-shrink: 0;
    line-height: 1;
  }

  .def-body h3 {
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--color-electric);
    margin-bottom: var(--spacing-sm);
  }

  .def-body p {
    font-size: 0.9rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .def-body strong {
    color: var(--color-neutral-light);
    opacity: 1;
    font-weight: 700;
  }

  /* Analogy card */
  .analogy-card {
    padding: var(--spacing-xl);
  }

  .analogy-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    margin-bottom: var(--spacing-md);
  }

  .analogy-icon { font-size: 1.5rem; }

  .analogy-label {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.12em;
    color: var(--color-electric);
    opacity: 0.8;
  }

  .analogy-card p {
    font-size: 0.88rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.65;
    margin-bottom: 0;
  }

  .analogy-card strong {
    color: var(--color-electric);
    opacity: 1;
    font-weight: 700;
  }

  /* Code block */
  .code-block {
    padding: 0;
    overflow: hidden;
    background: rgba(10, 22, 40, 0.6);
  }

  .code-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(30, 58, 138, 0.3);
    border-bottom: 1px solid rgba(96, 165, 250, 0.1);
  }

  .code-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
  }

  .code-dot.red    { background: #ff5f57; }
  .code-dot.yellow { background: #ffbd2e; }
  .code-dot.green  { background: #28c840; }

  .code-filename {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    color: var(--color-electric);
    opacity: 0.7;
    margin-left: var(--spacing-sm);
  }

  .code-content {
    padding: var(--spacing-lg);
    margin: 0;
    font-family: var(--font-mono);
    font-size: 0.78rem;
    line-height: 1.7;
    color: var(--color-neutral-light);
    opacity: 0.85;
    white-space: pre;
    overflow-x: auto;
  }

  .token-comment {
    color: var(--color-electric);
    opacity: 0.7;
    font-style: italic;
  }

  /* Key points */
  .key-points {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .key-point {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(30, 58, 138, 0.15);
    border: 1px solid rgba(96, 165, 250, 0.12);
    border-radius: var(--radius-sm);
  }

  .kp-icon { font-size: 1rem; flex-shrink: 0; }

  .kp-text {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.5;
  }

  .kp-text em {
    color: var(--color-electric);
    font-style: normal;
    font-weight: 600;
  }

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

    .subtitle {
      font-size: 0.9rem;
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .definition-card {
      padding: var(--spacing-lg);
      gap: var(--spacing-md);
    }

    .def-icon { font-size: 1.8rem; }

    .def-body h3 { font-size: 1rem; }

    .def-body p { font-size: 0.85rem; }

    .analogy-card {
      padding: var(--spacing-lg);
    }

    .analogy-icon { font-size: 1.3rem; }

    .analogy-card p { font-size: 0.82rem; }

    .code-header {
      padding: var(--spacing-md);
    }

    .code-content {
      padding: var(--spacing-md);
      font-size: 0.72rem;
    }

    .key-point {
      padding: var(--spacing-md);
      min-height: 44px;
      align-items: center;
    }

    .kp-icon { font-size: 0.9rem; }

    .kp-text { font-size: 0.8rem; }
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

    .subtitle {
      font-size: 0.8rem;
    }

    .definition-card {
      padding: var(--spacing-md);
      flex-direction: column;
      gap: var(--spacing-sm);
    }

    .def-icon {
      font-size: 1.5rem;
    }

    .def-body h3 {
      font-size: 0.95rem;
      margin-bottom: var(--spacing-xs);
    }

    .def-body p {
      font-size: 0.8rem;
    }

    .analogy-card {
      padding: var(--spacing-md);
    }

    .analogy-header {
      gap: var(--spacing-xs);
      margin-bottom: var(--spacing-sm);
    }

    .analogy-icon { font-size: 1.2rem; }

    .analogy-label { font-size: 0.7rem; }

    .analogy-card p { font-size: 0.78rem; }

    .code-header {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-xs);
    }

    .code-dot {
      width: 8px;
      height: 8px;
    }

    .code-filename {
      font-size: 0.7rem;
    }

    .code-content {
      padding: var(--spacing-sm) var(--spacing-md);
      font-size: 0.68rem;
      line-height: 1.6;
    }

    .key-point {
      padding: var(--spacing-sm) var(--spacing-md);
      min-height: 44px;
      gap: var(--spacing-sm);
    }

    .kp-icon { font-size: 0.85rem; }

    .kp-text { font-size: 0.75rem; }
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

    .subtitle {
      font-size: 0.75rem;
    }

    .definition-card {
      padding: var(--spacing-sm);
    }

    .def-icon { font-size: 1.3rem; }

    .def-body h3 { font-size: 0.9rem; }

    .def-body p { font-size: 0.75rem; }

    .analogy-card {
      padding: var(--spacing-sm);
    }

    .analogy-icon { font-size: 1.1rem; }

    .analogy-card p { font-size: 0.72rem; }

    .code-header {
      padding: var(--spacing-sm);
    }

    .code-dot {
      width: 6px;
      height: 6px;
    }

    .code-content {
      padding: var(--spacing-sm);
      font-size: 0.62rem;
    }

    .key-point {
      padding: var(--spacing-sm);
      min-height: 44px;
    }

    .kp-icon { font-size: 0.8rem; }

    .kp-text { font-size: 0.7rem; }
  }

  /* Short desktop screens: compress vertical spacing so content fits without scroll */
  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 12px var(--spacing-content);
      gap: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.6rem, 3.5vw, 2.4rem);
    }

    .main-layout {
      gap: var(--spacing-sm);
    }

    .left-col, .right-col {
      gap: var(--spacing-sm);
    }

    .definition-card {
      padding: var(--spacing-md);
      gap: var(--spacing-md);
    }

    .analogy-card {
      padding: var(--spacing-md);
    }

    .key-point {
      padding: var(--spacing-sm) var(--spacing-md);
    }
  }

  /* Short desktop screens: compress vertical spacing so content fits without scroll */
  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 12px var(--spacing-content);
      gap: var(--spacing-md);
    }

    .slide-header {
      margin-bottom: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.6rem, 3.5vw, 2.4rem);
    }

    .subtitle {
      font-size: 0.95rem;
    }

    .main-layout {
      gap: var(--spacing-md);
    }

    .left-col,
    .right-col {
      gap: var(--spacing-md);
    }

    .definition-card {
      padding: var(--spacing-md);
      gap: var(--spacing-md);
    }

    .def-icon {
      font-size: 1.8rem;
    }

    .def-body h3 {
      font-size: 1rem;
    }

    .def-body p {
      font-size: 0.85rem;
    }

    .analogy-card {
      padding: var(--spacing-md);
    }

    .analogy-card p {
      font-size: 0.82rem;
    }

    .code-header {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .code-content {
      padding: var(--spacing-md);
      font-size: 0.72rem;
    }

    .key-point {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .kp-text {
      font-size: 0.8rem;
    }
  }
</style>
