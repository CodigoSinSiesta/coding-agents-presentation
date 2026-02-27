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
      <span class="label">Orquestación</span>
      <h2 class="title">Agentes y <span class="highlight">Sub-agentes</span></h2>
      <p class="subtitle">Divide y vencerás. Pero con criterio.</p>
    </div>

    <div class="main-layout">
      <!-- Architecture diagram -->
      <div class="diagram-section">
        <div class="orchestrator card-glass">
          <div class="orch-icon">🎯</div>
          <div class="orch-body">
            <span class="orch-label">Orquestador</span>
            <span class="orch-desc">Recibe la tarea principal, la descompone y delega</span>
          </div>
        </div>

        <div class="arrows-row">
          <div class="arrow-line"></div>
          <div class="arrow-line"></div>
          <div class="arrow-line"></div>
        </div>

        <div class="subagents-row">
          <div class="subagent card-glass">
            <span class="sub-icon">📁</span>
            <span class="sub-name">File Agent</span>
            <span class="sub-task">Leer / escribir código</span>
          </div>
          <div class="subagent card-glass">
            <span class="sub-icon">🧪</span>
            <span class="sub-name">Test Agent</span>
            <span class="sub-task">Generar y ejecutar tests</span>
          </div>
          <div class="subagent card-glass">
            <span class="sub-icon">🔍</span>
            <span class="sub-name">Review Agent</span>
            <span class="sub-task">Code review + feedback</span>
          </div>
        </div>

        <div class="result-arrow">↓ resultados consolidados ↓</div>

        <div class="result-box card-glass">
          <span class="result-icon">✅</span>
          <span class="result-text">Respuesta final al desarrollador</span>
        </div>
      </div>

      <!-- Right: when and why -->
      <div class="right-col">
        <div class="when-card card-glass">
          <h3>¿Cuándo usar sub-agentes?</h3>
          <ul class="checklist">
            <li>
              <span class="check">✓</span>
              <span>La tarea es compleja y tiene partes independientes</span>
            </li>
            <li>
              <span class="check">✓</span>
              <span>Necesitas paralelismo real (varios archivos a la vez)</span>
            </li>
            <li>
              <span class="check">✓</span>
              <span>Quieres aislar responsabilidades y reducir errores</span>
            </li>
            <li>
              <span class="check warn">✗</span>
              <span class="warn-text">NO para tareas simples. Añade overhead y complejidad innecesaria</span>
            </li>
          </ul>
        </div>

        <div class="example-card card-glass">
          <div class="example-header">
            <span class="ex-icon">💡</span>
            <span class="ex-label">Ejemplo real en Claude Code</span>
          </div>
          <pre class="ex-code"><code><span class="c">// Claude Code lanza sub-agentes para:</span>
1. Explorar el codebase (explore agent)
2. Planificar cambios (plan agent)
3. Implementar en paralelo (build agents)
4. Verificar resultados (verify agent)</code></pre>
        </div>

        <div class="warning-card">
          <span class="warn-icon">⚠️</span>
          <p><strong>Ojo con el contexto:</strong> Cada sub-agente tiene su propia ventana de contexto. El orquestador debe pasar exactamente la información que necesita cada uno. Ni más, ni menos.</p>
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
      radial-gradient(ellipse at 30% 20%, rgba(59, 130, 246, 0.08) 0%, transparent 55%),
      radial-gradient(ellipse at 80% 80%, rgba(30, 58, 138, 0.1) 0%, transparent 55%);
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
    font-size: 1rem;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: 0;
    font-family: var(--font-mono);
  }

  /* Main layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.2fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  /* Diagram */
  .diagram-section {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-sm);
  }

  .orchestrator {
    display: flex;
    align-items: center;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
    width: 100%;
    border-color: rgba(59, 130, 246, 0.4);
    background: rgba(30, 58, 138, 0.25);
  }

  .orch-icon { font-size: 2rem; flex-shrink: 0; }

  .orch-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .orch-label {
    font-family: var(--font-display);
    font-size: 1.1rem;
    font-weight: 800;
    color: var(--color-electric);
  }

  .orch-desc {
    font-size: 0.8rem;
    color: var(--color-neutral-light);
    opacity: 0.65;
  }

  .arrows-row {
    display: flex;
    justify-content: space-around;
    width: 80%;
    padding: var(--spacing-xs) 0;
  }

  .arrow-line {
    width: 2px;
    height: 24px;
    background: linear-gradient(to bottom, rgba(96, 165, 250, 0.6), rgba(96, 165, 250, 0.1));
    position: relative;
  }

  .arrow-line::after {
    content: '▼';
    position: absolute;
    bottom: -14px;
    left: 50%;
    transform: translateX(-50%);
    font-size: 0.6rem;
    color: var(--color-electric);
    opacity: 0.5;
  }

  .subagents-row {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-sm);
    width: 100%;
  }

  .subagent {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: var(--spacing-xs);
    padding: var(--spacing-md);
    text-align: center;
  }

  .sub-icon { font-size: 1.5rem; }

  .sub-name {
    font-family: var(--font-display);
    font-size: 0.85rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .sub-task {
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.7;
    font-family: var(--font-mono);
    line-height: 1.4;
  }

  .result-arrow {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.5;
    text-align: center;
    padding: var(--spacing-xs) 0;
  }

  .result-box {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-xl);
    width: 100%;
    justify-content: center;
    border-color: rgba(40, 200, 64, 0.3);
    background: rgba(40, 200, 64, 0.05);
  }

  .result-icon { font-size: 1.2rem; }

  .result-text {
    font-size: 0.9rem;
    font-weight: 600;
    color: var(--color-neutral-light);
    font-family: var(--font-display);
  }

  /* Right col */
  .right-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  .when-card {
    padding: var(--spacing-xl);
  }

  .when-card h3 {
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-electric);
    margin-bottom: var(--spacing-lg);
  }

  .checklist {
    list-style: none;
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .checklist li {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.85;
    line-height: 1.5;
  }

  .check {
    font-family: var(--font-mono);
    font-weight: 800;
    font-size: 0.9rem;
    color: #28c840;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .check.warn { color: #ff5f57; }
  .warn-text { opacity: 0.65 !important; }

  /* Example card */
  .example-card {
    padding: 0;
    overflow: hidden;
    background: rgba(10, 22, 40, 0.5);
  }

  .example-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(30, 58, 138, 0.3);
    border-bottom: 1px solid rgba(96, 165, 250, 0.1);
  }

  .ex-icon { font-size: 1rem; }

  .ex-label {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.8;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .ex-code {
    padding: var(--spacing-lg);
    margin: 0;
    font-family: var(--font-mono);
    font-size: 0.78rem;
    line-height: 1.7;
    color: var(--color-neutral-light);
    opacity: 0.85;
  }

  .c {
    color: var(--color-electric);
    opacity: 0.6;
    font-style: italic;
  }

  /* Warning */
  .warning-card {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(255, 189, 46, 0.05);
    border: 1px solid rgba(255, 189, 46, 0.25);
    border-radius: var(--radius-sm);
  }

  .warn-icon { font-size: 1.2rem; flex-shrink: 0; }

  .warning-card p {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.55;
    margin-bottom: 0;
  }

  .warning-card strong { color: #ffbd2e; font-weight: 700; }

  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
  }
</style>
