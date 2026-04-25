<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const factors = [
    { num: '01', title: 'NL → Tool Calls', desc: 'El LLM convierte lenguaje en JSON validable.' },
    { num: '02', title: 'Own your prompts', desc: 'Versiona tus prompts como código fuente.' },
    { num: '03', title: 'Own your context', desc: 'Tú decides qué entra. La librería no es caja negra.' },
    { num: '04', title: 'Tools = structured outputs', desc: 'La tool call es JSON. La lógica vive en tu código.' },
    { num: '05', title: 'Unify state', desc: 'Estado del agente = estado de tu negocio.' },
    { num: '06', title: 'Launch / Pause / Resume', desc: 'Tu agente se para y reanuda como cualquier proceso.' },
    { num: '07', title: 'Contact humans as tools', desc: 'El humano-en-el-loop también es una tool call.' },
    { num: '08', title: 'Own your control flow', desc: 'Si conoces el workflow, no lo metas en el prompt.' },
    { num: '09', title: 'Compact errors', desc: 'Error → mensaje corto accionable, no volcado.' },
    { num: '10', title: 'Small focused agents', desc: 'Mejor varios micro-agentes que un mega-agente.' },
    { num: '11', title: 'Trigger anywhere', desc: 'Slack, cron, webhook, email. Donde el usuario vive.' },
    { num: '12', title: 'Stateless reducer', desc: 'nuevo_estado = agente(estado, evento). Replay trivial.' },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">Para producción</span>
      <h2 class="title">Los <span class="highlight">12 factores</span> de un agente</h2>
      <p class="subtitle">Los buenos agentes son sobre todo software bien escrito.</p>
    </div>

    <div class="thesis card-glass">
      <span class="thesis-icon">📐</span>
      <p>Dexter Horthy (HumanLayer) tras hablar con +100 fundadores: <strong>todos chocan al 70-80% de calidad</strong> usando frameworks. Frente a la rendición ("rewrite desde cero"), propone 12 principios modulares para incrustar en software existente. En el espíritu de los 12 Factor Apps.</p>
    </div>

    <div class="factors-grid">
      {#each factors as factor}
        <div class="factor card-glass">
          <span class="factor-num">{factor.num}</span>
          <div class="factor-body">
            <span class="factor-title">{factor.title}</span>
            <span class="factor-desc">{factor.desc}</span>
          </div>
        </div>
      {/each}
    </div>

    <div class="key-insight">
      <span class="insight-icon">💡</span>
      <p>"La mayoría de productos que se anuncian como AI Agents son <strong>código determinista con pasos LLM espolvoreados en el sitio justo</strong>." — Dexter Horthy, HumanLayer</p>
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
      radial-gradient(ellipse at 20% 30%, rgba(96, 165, 250, 0.08) 0%, transparent 55%),
      radial-gradient(ellipse at 85% 75%, rgba(30, 58, 138, 0.12) 0%, transparent 55%);
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
    gap: var(--spacing-lg);
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

  /* Thesis */
  .thesis {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
  }

  .thesis-icon { font-size: 1.4rem; flex-shrink: 0; margin-top: 2px; }

  .thesis p {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.82;
    line-height: 1.6;
    margin-bottom: 0;
  }

  .thesis strong { color: var(--color-electric); font-weight: 700; opacity: 1; }

  /* Factors grid */
  .factors-grid {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: var(--spacing-sm);
  }

  .factor {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-sm);
    padding: var(--spacing-sm) var(--spacing-md);
  }

  .factor-num {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    font-weight: 800;
    color: var(--color-accent-bright);
    opacity: 0.7;
    flex-shrink: 0;
    margin-top: 1px;
  }

  .factor-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .factor-title {
    font-family: var(--font-display);
    font-size: 0.82rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    line-height: 1.2;
  }

  .factor-desc {
    font-size: 0.7rem;
    color: var(--color-neutral-light);
    opacity: 0.6;
    line-height: 1.4;
  }

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

  .key-insight strong { color: var(--color-electric); font-style: normal; font-weight: 700; opacity: 1; }

  /* Mobile: Tablet */
  @media (max-width: 900px) {
    .factors-grid { grid-template-columns: repeat(2, 1fr); }
  }

  /* Mobile: Small tablet / large phone */
  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-md);
    }

    .title { font-size: clamp(1.6rem, 5vw, 2.4rem); }
    .subtitle { font-size: 0.9rem; }

    .thesis { padding: var(--spacing-md); }
    .thesis-icon { font-size: 1.2rem; }
    .thesis p { font-size: 0.8rem; }

    .factor { padding: var(--spacing-sm); }
    .factor-title { font-size: 0.78rem; }
    .factor-desc { font-size: 0.68rem; }

    .key-insight { padding: var(--spacing-md); gap: var(--spacing-sm); }
    .key-insight p { font-size: 0.8rem; }
  }

  /* Mobile: Phone */
  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-sm);
    }

    .label { font-size: 0.7rem; }
    .title { font-size: clamp(1.4rem, 6vw, 1.8rem); }
    .subtitle { font-size: 0.8rem; }

    .factors-grid { grid-template-columns: 1fr; }

    .thesis { padding: var(--spacing-sm) var(--spacing-md); }
    .thesis p { font-size: 0.78rem; }

    .factor { padding: var(--spacing-sm) var(--spacing-md); min-height: 48px; }
    .factor-title { font-size: 0.82rem; }
    .factor-desc { font-size: 0.7rem; }

    .key-insight { padding: var(--spacing-sm) var(--spacing-md); }
    .key-insight p { font-size: 0.74rem; }
  }

  /* Mobile: Small phone */
  @media (max-width: 390px) {
    .slide-content { padding: var(--spacing-sm); }

    .title { font-size: clamp(1.2rem, 6vw, 1.6rem); }
    .subtitle { font-size: 0.75rem; }

    .thesis p { font-size: 0.72rem; }
    .factor-title { font-size: 0.78rem; }
    .factor-desc { font-size: 0.66rem; }
    .key-insight p { font-size: 0.7rem; }
  }

  /* Short desktop screens: compress spacing */
  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 12px var(--spacing-content);
      gap: var(--spacing-sm);
    }

    .title { font-size: clamp(1.6rem, 3.5vw, 2.4rem); }

    .thesis { padding: var(--spacing-sm) var(--spacing-md); }
    .thesis p { font-size: 0.8rem; }

    .factor { padding: var(--spacing-xs) var(--spacing-sm); }
    .factor-title { font-size: 0.78rem; }
    .factor-desc { font-size: 0.68rem; line-height: 1.3; }

    .key-insight { padding: var(--spacing-sm) var(--spacing-md); }
    .key-insight p { font-size: 0.78rem; }
  }
</style>
