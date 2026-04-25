<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const pillars = [
    {
      icon: '🆓',
      title: 'Code is free',
      desc: 'Producir, refactorizar y borrar código deja de ser escaso. Cada engineer tiene 5-50-5.000 colaboradores 24/7. La migración de 6 meses se cierra lanzando 15 agentes.',
    },
    {
      icon: '🧠',
      title: 'Recursos escasos: tiempo, atención, contexto',
      desc: 'El cuello de botella ya no es teclear. Es la atención humana, la del modelo y el context window. Hay que estructurar el repo para gastarlos bien.',
    },
    {
      icon: '📚',
      title: 'El repo es prompt persistente',
      desc: 'Cada lint, test, error message y reviewer agent es prompt que se reactiva cuando toca. Escríbelo una vez, durabilidad infinita.',
    },
  ];

  const practices = [
    {
      title: 'Reviewer agents por persona',
      desc: 'Cada engineer documenta su rol (front-end, reliability, scalability). Un agent por persona se ejecuta en CI bloqueando merges con esa lente.',
    },
    {
      title: 'Garbage Collection Friday',
      desc: 'Una vez a la semana, todo el equipo convierte feedback humano en lints, tests y docs que ningún agente vuelva a saltarse.',
    },
    {
      title: 'Skills para escribir prompts',
      desc: 'Cuando escribir prompts a mano se repite, shellea al agente con una skill que los genere a partir de cookbooks.',
    },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El siguiente nivel</span>
      <h2 class="title">Harness <span class="highlight">Engineering</span></h2>
      <p class="subtitle">Tu nuevo rol: operacionalizar el repo para un ejército de agentes.</p>
    </div>

    <div class="quote-block">
      <span class="quote-mark">"</span>
      <p>La implementación ya no es el recurso escaso. <strong>El código es libre</strong>: gratis de producir, refactorizar y borrar. No es algo que merezca preocupar más.</p>
      <span class="quote-author">— Ryan Lopopolo, OpenAI · token billionaire</span>
    </div>

    <div class="main-grid">
      <!-- Three pillars -->
      <div class="pillars-col">
        <h3 class="col-title">Las 3 ideas matriz</h3>
        {#each pillars as pillar}
          <div class="pillar card-glass">
            <span class="pillar-icon">{pillar.icon}</span>
            <div class="pillar-body">
              <span class="pillar-title">{pillar.title}</span>
              <span class="pillar-desc">{pillar.desc}</span>
            </div>
          </div>
        {/each}
      </div>

      <!-- Operational practices -->
      <div class="practices-col">
        <h3 class="col-title">Patrones operativos</h3>
        {#each practices as p, i}
          <div class="practice card-glass">
            <span class="practice-num">0{i + 1}</span>
            <div class="practice-body">
              <span class="practice-title">{p.title}</span>
              <span class="practice-desc">{p.desc}</span>
            </div>
          </div>
        {/each}

        <div class="convergence">
          <span class="conv-icon">🎯</span>
          <p>Mismo patrón emergente en <strong>OpenAI</strong> (Lopopolo), <strong>Y Combinator</strong> (Garry Tan / gstack) y <strong>HumanLayer</strong> (Horthy / 12-factor). Persona-based review se ha vuelto pieza estable.</p>
        </div>
      </div>
    </div>

    <div class="bottom-insight">
      <span class="insight-icon">⚡</span>
      <p>"Cada vez que tienes que decirle <strong>'continúa'</strong> al agente es un fallo del harness." Si la sesión necesita ese empujón, lo que falla es la información que el harness pone delante del agente.</p>
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
      radial-gradient(ellipse at 75% 25%, rgba(168, 139, 250, 0.08) 0%, transparent 55%),
      radial-gradient(ellipse at 15% 75%, rgba(30, 58, 138, 0.12) 0%, transparent 55%);
    z-index: 1;
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 1280px;
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
    background: linear-gradient(135deg, #a78bfa, var(--color-accent-bright));
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

  /* Quote */
  .quote-block {
    position: relative;
    padding: var(--spacing-md) var(--spacing-xl);
    background: rgba(167, 139, 250, 0.06);
    border-left: 3px solid #a78bfa;
    border-radius: var(--radius-sm);
  }

  .quote-mark {
    position: absolute;
    top: -10px;
    left: var(--spacing-md);
    font-family: var(--font-display);
    font-size: 3rem;
    color: #a78bfa;
    opacity: 0.5;
    line-height: 1;
  }

  .quote-block p {
    font-size: 0.95rem;
    color: var(--color-neutral-light);
    opacity: 0.88;
    line-height: 1.55;
    margin-bottom: var(--spacing-xs);
    font-style: italic;
  }

  .quote-block strong { color: #a78bfa; font-weight: 800; opacity: 1; }

  .quote-author {
    display: block;
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.65;
    text-align: right;
  }

  /* Main grid */
  .main-grid {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  .col-title {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    text-transform: uppercase;
    letter-spacing: 0.1em;
    color: var(--color-electric);
    opacity: 0.7;
    margin-bottom: var(--spacing-md);
  }

  .pillars-col, .practices-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  /* Pillar */
  .pillar {
    display: flex;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    align-items: flex-start;
  }

  .pillar-icon { font-size: 1.4rem; flex-shrink: 0; margin-top: 1px; }

  .pillar-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .pillar-title {
    font-family: var(--font-display);
    font-size: 0.92rem;
    font-weight: 800;
    color: var(--color-neutral-light);
  }

  .pillar-desc {
    font-size: 0.78rem;
    color: var(--color-neutral-light);
    opacity: 0.7;
    line-height: 1.5;
  }

  /* Practice */
  .practice {
    display: flex;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    align-items: flex-start;
  }

  .practice-num {
    font-family: var(--font-mono);
    font-size: 0.78rem;
    font-weight: 800;
    color: #a78bfa;
    opacity: 0.7;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .practice-body {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .practice-title {
    font-family: var(--font-display);
    font-size: 0.88rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .practice-desc {
    font-size: 0.76rem;
    color: var(--color-neutral-light);
    opacity: 0.7;
    line-height: 1.5;
  }

  /* Convergence note */
  .convergence {
    display: flex;
    gap: var(--spacing-sm);
    align-items: flex-start;
    padding: var(--spacing-sm) var(--spacing-md);
    background: rgba(167, 139, 250, 0.05);
    border: 1px dashed rgba(167, 139, 250, 0.25);
    border-radius: var(--radius-sm);
    margin-top: var(--spacing-xs);
  }

  .conv-icon { font-size: 0.95rem; flex-shrink: 0; margin-top: 1px; }

  .convergence p {
    font-size: 0.74rem;
    color: var(--color-neutral-light);
    opacity: 0.78;
    line-height: 1.5;
    margin-bottom: 0;
  }

  .convergence strong { color: #a78bfa; font-weight: 700; opacity: 1; }

  /* Bottom insight */
  .bottom-insight {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-md);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(59, 130, 246, 0.08);
    border: 1px solid rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-sm);
  }

  .insight-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 1px; }

  .bottom-insight p {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.85;
    line-height: 1.6;
    margin-bottom: 0;
    font-style: italic;
  }

  .bottom-insight strong { color: var(--color-electric); font-weight: 800; opacity: 1; font-style: normal; }

  /* Mobile: Tablet */
  @media (max-width: 900px) {
    .main-grid { grid-template-columns: 1fr; gap: var(--spacing-lg); }
  }

  /* Mobile: Small tablet / large phone */
  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-md);
    }

    .title { font-size: clamp(1.6rem, 5vw, 2.4rem); }
    .subtitle { font-size: 0.9rem; }

    .quote-block { padding: var(--spacing-md); }
    .quote-mark { font-size: 2.4rem; top: -8px; }
    .quote-block p { font-size: 0.85rem; }

    .pillar, .practice { padding: var(--spacing-md); }
    .pillar-icon { font-size: 1.2rem; }
    .pillar-title { font-size: 0.85rem; }
    .pillar-desc, .practice-desc { font-size: 0.74rem; }

    .convergence p { font-size: 0.7rem; }

    .bottom-insight { padding: var(--spacing-md); gap: var(--spacing-sm); }
    .bottom-insight p { font-size: 0.8rem; }
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

    .quote-block { padding: var(--spacing-sm) var(--spacing-md); }
    .quote-block p { font-size: 0.78rem; }
    .quote-author { font-size: 0.65rem; }

    .pillar, .practice { padding: var(--spacing-sm) var(--spacing-md); gap: var(--spacing-sm); }
    .pillar-title { font-size: 0.82rem; }
    .practice-title { font-size: 0.82rem; }
    .pillar-desc, .practice-desc { font-size: 0.7rem; }

    .convergence { padding: var(--spacing-sm); }
    .convergence p { font-size: 0.68rem; }

    .bottom-insight { padding: var(--spacing-sm) var(--spacing-md); }
    .bottom-insight p { font-size: 0.74rem; }
  }

  /* Mobile: Small phone */
  @media (max-width: 390px) {
    .slide-content { padding: var(--spacing-sm); }
    .title { font-size: clamp(1.2rem, 6vw, 1.6rem); }
    .subtitle { font-size: 0.75rem; }

    .quote-block p { font-size: 0.74rem; }
    .pillar-title, .practice-title { font-size: 0.78rem; }
    .pillar-desc, .practice-desc { font-size: 0.66rem; }
    .bottom-insight p { font-size: 0.7rem; }
  }

  /* Short desktop screens: compress spacing */
  @media (max-height: 900px) and (min-width: 769px) {
    .slide-content {
      padding: 12px var(--spacing-content);
      gap: var(--spacing-sm);
    }

    .title { font-size: clamp(1.6rem, 3.5vw, 2.4rem); }

    .quote-block { padding: var(--spacing-sm) var(--spacing-lg); }
    .quote-block p { font-size: 0.85rem; }

    .pillar, .practice { padding: var(--spacing-sm) var(--spacing-md); }
    .pillar-desc, .practice-desc { font-size: 0.74rem; line-height: 1.4; }

    .pillars-col, .practices-col { gap: var(--spacing-xs); }

    .bottom-insight { padding: var(--spacing-sm) var(--spacing-md); }
    .bottom-insight p { font-size: 0.78rem; }
  }
</style>
