<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const demoSteps = [
    { n: '01', icon: '📋', title: 'CLAUDE.md', desc: 'Definimos el contexto del proyecto: arquitectura, stack, reglas.' },
    { n: '02', icon: '💬', title: 'Prompt claro', desc: 'Instrucción específica con scope definido y criterio de éxito.' },
    { n: '03', icon: '🔄', title: 'Agente trabaja', desc: 'Lee archivos, razona, hace tool calls, genera el código.' },
    { n: '04', icon: '🔍', title: 'Revisión crítica', desc: 'Verificamos, corremos tests, iteramos si es necesario.' },
  ];

  const workflow = [
    { label: 'Explorar', cmd: 'Analiza la estructura del proyecto', icon: '🔭' },
    { label: 'Planificar', cmd: 'Qué cambios necesitamos y por qué', icon: '📐' },
    { label: 'Implementar', cmd: 'Genera el código siguiendo la arquitectura', icon: '⚡' },
    { label: 'Verificar', cmd: 'Corre los tests y valida', icon: '✅' },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Hands on</span>
      <h2 class="title">Flujo de trabajo <span class="highlight">real</span></h2>
      <p class="subtitle">Así se trabaja con Claude Code en el día a día.</p>
    </div>

    <div class="main-layout">
      <!-- Left: demo steps -->
      <div class="left-col">
        <div class="steps-card card-glass">
          <h3 class="steps-title">Los 4 pasos que siempre uso</h3>
          <div class="steps-list">
            {#each demoSteps as step}
              <div class="demo-step">
                <div class="step-num">{step.n}</div>
                <div class="step-content">
                  <div class="step-header">
                    <span class="step-icon">{step.icon}</span>
                    <span class="step-title">{step.title}</span>
                  </div>
                  <p class="step-desc">{step.desc}</p>
                </div>
              </div>
            {/each}
          </div>
        </div>
      </div>

      <!-- Right: workflow + terminal mockup -->
      <div class="right-col">
        <div class="workflow-chain card-glass">
          <h3 class="wf-title">Pipeline de trabajo</h3>
          <div class="wf-steps">
            {#each workflow as step, i}
              <div class="wf-step">
                <div class="wf-icon">{step.icon}</div>
                <div class="wf-body">
                  <span class="wf-label">{step.label}</span>
                  <span class="wf-cmd">"{step.cmd}"</span>
                </div>
              </div>
              {#if i < workflow.length - 1}
                <div class="wf-arrow">→</div>
              {/if}
            {/each}
          </div>
        </div>

        <div class="terminal card-glass">
          <div class="terminal-header">
            <span class="t-dot red"></span>
            <span class="t-dot yellow"></span>
            <span class="t-dot green"></span>
            <span class="t-title">claude-code</span>
          </div>
          <div class="terminal-body">
            <div class="t-line"><span class="t-prompt">$</span><span class="t-cmd"> claude</span></div>
            <div class="t-line t-response">✓ Claude Code iniciado</div>
            <div class="t-line t-response">✓ Leyendo CLAUDE.md...</div>
            <div class="t-line"><span class="t-prompt">›</span><span class="t-input"> Refactoriza el servicio de usuarios siguiendo Clean Architecture</span></div>
            <div class="t-line t-agent">⟳ Analizando estructura del proyecto...</div>
            <div class="t-line t-agent">⟳ Leyendo src/users/... (3 archivos)</div>
            <div class="t-line t-agent">⟳ Generando casos de uso...</div>
            <div class="t-line t-success">✓ Completado: 4 archivos modificados, tests incluidos</div>
          </div>
        </div>

        <div class="reminder-box">
          <span class="reminder-icon">⚠️</span>
          <p>Esta presentación ha sido creada <strong>en tiempo real</strong> usando Claude Code. Lo que ves es el producto del flujo que acabas de aprender.</p>
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
      radial-gradient(ellipse at 20% 20%, rgba(59, 130, 246, 0.1) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 80%, rgba(30, 58, 138, 0.12) 0%, transparent 55%);
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

  /* Demo steps */
  .steps-card {
    padding: var(--spacing-xl);
  }

  .steps-title {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: var(--spacing-lg);
  }

  .steps-list {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .demo-step {
    display: flex;
    gap: var(--spacing-lg);
    align-items: flex-start;
  }

  .step-num {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    font-weight: 800;
    color: var(--color-electric);
    opacity: 0.5;
    flex-shrink: 0;
    padding-top: 3px;
  }

  .step-content { flex: 1; }

  .step-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    margin-bottom: 4px;
  }

  .step-icon { font-size: 1rem; }

  .step-title {
    font-family: var(--font-display);
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .step-desc {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.65;
    line-height: 1.5;
    margin-bottom: 0;
    padding-left: calc(1rem + var(--spacing-sm));
  }

  /* Workflow chain */
  .workflow-chain {
    padding: var(--spacing-xl);
  }

  .wf-title {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: var(--spacing-lg);
  }

  .wf-steps {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    flex-wrap: wrap;
  }

  .wf-step {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding: var(--spacing-sm) var(--spacing-md);
    background: rgba(59, 130, 246, 0.08);
    border: 1px solid rgba(96, 165, 250, 0.15);
    border-radius: var(--radius-sm);
    flex: 1;
    min-width: 0;
  }

  .wf-icon { font-size: 1.2rem; flex-shrink: 0; }

  .wf-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
    min-width: 0;
  }

  .wf-label {
    font-family: var(--font-display);
    font-size: 0.82rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .wf-cmd {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--color-electric);
    opacity: 0.8;
  }

  .wf-arrow {
    color: var(--color-electric);
    opacity: 0.4;
    font-size: 1rem;
    flex-shrink: 0;
  }

  /* Terminal */
  .terminal {
    padding: 0;
    overflow: hidden;
    background: rgba(5, 12, 26, 0.8);
    border-color: rgba(96, 165, 250, 0.15);
  }

  .terminal-header {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(30, 58, 138, 0.3);
    border-bottom: 1px solid rgba(96, 165, 250, 0.1);
  }

  .t-dot {
    width: 10px;
    height: 10px;
    border-radius: 50%;
  }

  .t-dot.red    { background: #ff5f57; }
  .t-dot.yellow { background: #ffbd2e; }
  .t-dot.green  { background: #28c840; }

  .t-title {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.6;
    margin-left: var(--spacing-sm);
  }

  .terminal-body {
    padding: var(--spacing-lg);
    display: flex;
    flex-direction: column;
    gap: 6px;
  }

  .t-line {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    line-height: 1.5;
    color: var(--color-neutral-light);
    opacity: 0.8;
  }

  .t-prompt { color: #34d399; margin-right: 6px; }
  .t-cmd    { color: var(--color-electric); }
  .t-input  { color: var(--color-neutral-light); opacity: 0.9; }
  .t-response { color: var(--color-electric); opacity: 0.6; }
  .t-agent  { color: #f59e0b; opacity: 0.8; }
  .t-success { color: #34d399; font-weight: 600; opacity: 1; }

  /* Reminder */
  .reminder-box {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(59, 130, 246, 0.08);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-sm);
    border-style: dashed;
  }

  .reminder-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 2px; }

  .reminder-box p {
    font-size: 0.82rem;
    color: var(--color-neutral-light);
    opacity: 0.8;
    line-height: 1.6;
    margin-bottom: 0;
    font-style: italic;
  }

  .reminder-box strong { color: var(--color-electric); font-style: normal; font-weight: 700; }

  /* Mobile: Tablet */
  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
    .wf-steps { flex-direction: column; }
    .wf-step { width: 100%; flex: none; }
    .wf-arrow { transform: rotate(90deg); }
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

    .subtitle {
      font-size: 0.9rem;
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .steps-card {
      padding: var(--spacing-lg);
    }

    .steps-title {
      font-size: 0.72rem;
      margin-bottom: var(--spacing-md);
    }

    .demo-step {
      gap: var(--spacing-md);
      min-height: 44px;
    }

    .step-num {
      font-size: 0.68rem;
      padding-top: 2px;
    }

    .step-title {
      font-size: 0.9rem;
    }

    .step-desc {
      font-size: 0.78rem;
      padding-left: calc(1rem + var(--spacing-sm));
    }

    .workflow-chain {
      padding: var(--spacing-lg);
    }

    .wf-title {
      font-size: 0.72rem;
      margin-bottom: var(--spacing-md);
    }

    .wf-step {
      padding: var(--spacing-sm);
    }

    .wf-icon {
      font-size: 1rem;
    }

    .wf-label {
      font-size: 0.78rem;
    }

    .wf-cmd {
      font-size: 0.65rem;
    }

    .terminal-header {
      padding: var(--spacing-md);
    }

    .t-title {
      font-size: 0.68rem;
    }

    .terminal-body {
      padding: var(--spacing-md);
      overflow-x: auto;
    }

    .t-line {
      font-size: 0.72rem;
    }

    .reminder-box {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .reminder-icon {
      font-size: 1rem;
    }

    .reminder-box p {
      font-size: 0.78rem;
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

    .subtitle {
      font-size: 0.8rem;
    }

    .steps-card {
      padding: var(--spacing-md);
    }

    .steps-title {
      font-size: 0.68rem;
      margin-bottom: var(--spacing-sm);
    }

    .steps-list {
      gap: var(--spacing-sm);
    }

    .demo-step {
      gap: var(--spacing-sm);
      min-height: 44px;
    }

    .step-num {
      font-size: 0.65rem;
    }

    .step-icon {
      font-size: 0.9rem;
    }

    .step-title {
      font-size: 0.85rem;
    }

    .step-desc {
      font-size: 0.72rem;
      padding-left: 1rem;
    }

    .workflow-chain {
      padding: var(--spacing-md);
    }

    .wf-title {
      font-size: 0.65rem;
      margin-bottom: var(--spacing-sm);
    }

    .wf-step {
      padding: var(--spacing-xs) var(--spacing-sm);
    }

    .wf-icon {
      font-size: 0.9rem;
    }

    .wf-label {
      font-size: 0.75rem;
    }

    .wf-cmd {
      font-size: 0.62rem;
    }

    .terminal-header {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .t-dot {
      width: 8px;
      height: 8px;
    }

    .t-title {
      font-size: 0.65rem;
    }

    .terminal-body {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: 4px;
    }

    .t-line {
      font-size: 0.68rem;
    }

    .reminder-box {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .reminder-icon {
      font-size: 0.9rem;
    }

    .reminder-box p {
      font-size: 0.72rem;
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

    .subtitle {
      font-size: 0.75rem;
    }

    .steps-card {
      padding: var(--spacing-sm);
    }

    .steps-title {
      font-size: 0.62rem;
    }

    .demo-step {
      min-height: 44px;
    }

    .step-num {
      font-size: 0.6rem;
    }

    .step-icon {
      font-size: 0.85rem;
    }

    .step-title {
      font-size: 0.8rem;
    }

    .step-desc {
      font-size: 0.68rem;
    }

    .workflow-chain {
      padding: var(--spacing-sm);
    }

    .wf-title {
      font-size: 0.6rem;
    }

    .wf-icon {
      font-size: 0.85rem;
    }

    .wf-label {
      font-size: 0.72rem;
    }

    .wf-cmd {
      font-size: 0.58rem;
    }

    .terminal-header {
      padding: var(--spacing-xs) var(--spacing-sm);
    }

    .t-title {
      font-size: 0.6rem;
    }

    .terminal-body {
      padding: var(--spacing-sm);
    }

    .t-line {
      font-size: 0.62rem;
    }

    .reminder-box {
      padding: var(--spacing-sm);
    }

    .reminder-box p {
      font-size: 0.68rem;
    }
  }
</style>
