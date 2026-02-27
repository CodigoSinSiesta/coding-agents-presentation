<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const resources = [
    { label: 'Claude Code', url: 'claude.ai/code', icon: '🤖', desc: 'CLI oficial de Anthropic' },
    { label: 'Cursor', url: 'cursor.com', icon: '⚡', desc: 'IDE con agente nativo' },
    { label: 'Windsurf', url: 'codeium.com/windsurf', icon: '🌊', desc: 'IDE con Cascade' },
    { label: 'OpenCode', url: 'github.com/sst/opencode', icon: '🖥️', desc: 'CLI open source' },
  ];

  const takeaways = [
    'El agente es Jarvis, tú eres Tony Stark. Dirige.',
    'Sin System Prompt sólido, sin resultados predecibles.',
    'Contexto es poder. Dale al agente lo que necesita.',
    'Revisa siempre. El código no es tuyo hasta que lo entiendes.',
    'Las alucinaciones se previenen, no se aceptan.',
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="animated-grid"></div>

  <div class="slide-content">
    <div class="closing-header">
      <h2 class="title">
        El futuro del desarrollo<br />
        <span class="highlight">ya está aquí.</span><br />
        <span class="question">¿Estás preparado?</span>
      </h2>
    </div>

    <div class="main-layout">
      <!-- Takeaways -->
      <div class="takeaways-col">
        <h3 class="col-title">Para llevarte a casa</h3>
        <div class="takeaways-list">
          {#each takeaways as point, i}
            <div class="takeaway">
              <span class="ta-num">0{i + 1}</span>
              <span class="ta-text">{point}</span>
            </div>
          {/each}
        </div>
      </div>

      <!-- Resources + author -->
      <div class="right-col">
        <div class="resources card-glass">
          <h3 class="col-title">Recursos</h3>
          <div class="resources-list">
            {#each resources as res}
              <div class="resource-item">
                <span class="res-icon">{res.icon}</span>
                <div class="res-body">
                  <span class="res-label">{res.label}</span>
                  <span class="res-url">{res.url}</span>
                </div>
                <span class="res-desc">{res.desc}</span>
              </div>
            {/each}
          </div>
        </div>

        <div class="author-final card-glass">
          <div class="author-avatar">AL</div>
          <div class="author-body">
            <span class="author-name">Alejandro de la Fuente</span>
            <div class="author-links">
              <span class="author-link">🌐 tellmealex.dev</span>
              <span class="author-link">📺 YouTube: Código sin Siesta</span>
              <span class="author-link">🐦 @alexdevbytes</span>
            </div>
          </div>
        </div>

        <div class="final-quote">
          <span class="quote-icon">💬</span>
          <p>"La IA no te va a sustituir.<br />Te va a sustituir alguien que sabe usar la IA mejor que tú."</p>
        </div>
      </div>
    </div>
  </div>

  <!-- Orbs -->
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
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
      radial-gradient(ellipse at 10% 50%, rgba(59, 130, 246, 0.12) 0%, transparent 55%),
      radial-gradient(ellipse at 90% 40%, rgba(30, 58, 138, 0.15) 0%, transparent 55%);
    z-index: 1;
  }

  .animated-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(96, 165, 250, 0.06) 1px, transparent 1px),
      linear-gradient(90deg, rgba(96, 165, 250, 0.06) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
    animation: moveGrid 30s linear infinite;
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

  /* Header */
  .closing-header { text-align: center; }

  .title {
    font-size: clamp(2rem, 4.5vw, 3.2rem);
    font-weight: 900;
    color: var(--color-neutral-light);
    line-height: 1.2;
    margin-bottom: 0;
  }

  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  .question {
    opacity: 0.6;
    font-size: clamp(1.5rem, 3.5vw, 2.4rem);
  }

  /* Layout */
  .main-layout {
    display: grid;
    grid-template-columns: 1fr 1.1fr;
    gap: var(--spacing-xl);
    align-items: start;
  }

  .col-title {
    font-family: var(--font-mono);
    font-size: 0.75rem;
    text-transform: uppercase;
    letter-spacing: 0.15em;
    color: var(--color-electric);
    opacity: 0.7;
    margin-bottom: var(--spacing-lg);
  }

  /* Takeaways */
  .takeaways-col {
    display: flex;
    flex-direction: column;
  }

  .takeaways-list {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
  }

  .takeaway {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-lg);
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(30, 58, 138, 0.15);
    border: 1px solid rgba(96, 165, 250, 0.12);
    border-radius: var(--radius-sm);
    transition: all var(--transition-fast);
  }

  .takeaway:hover {
    background: rgba(30, 58, 138, 0.25);
    border-color: rgba(96, 165, 250, 0.25);
  }

  .ta-num {
    font-family: var(--font-mono);
    font-size: 0.7rem;
    font-weight: 800;
    color: var(--color-electric);
    opacity: 0.4;
    flex-shrink: 0;
    margin-top: 2px;
  }

  .ta-text {
    font-size: 0.88rem;
    color: var(--color-neutral-light);
    opacity: 0.85;
    line-height: 1.5;
  }

  /* Right col */
  .right-col {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-lg);
  }

  /* Resources */
  .resources {
    padding: var(--spacing-xl);
  }

  .resources-list {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .resource-item {
    display: flex;
    align-items: center;
    gap: var(--spacing-md);
    padding: var(--spacing-sm) var(--spacing-md);
    background: rgba(59, 130, 246, 0.05);
    border-radius: var(--radius-sm);
    border: 1px solid rgba(96, 165, 250, 0.08);
  }

  .res-icon { font-size: 1.1rem; flex-shrink: 0; }

  .res-body {
    display: flex;
    flex-direction: column;
    gap: 1px;
    flex: 1;
  }

  .res-label {
    font-family: var(--font-display);
    font-size: 0.88rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .res-url {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.65;
  }

  .res-desc {
    font-size: 0.75rem;
    color: var(--color-neutral-light);
    opacity: 0.45;
    white-space: nowrap;
    font-family: var(--font-mono);
  }

  /* Author */
  .author-final {
    display: flex;
    align-items: center;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
  }

  .author-avatar {
    width: 48px;
    height: 48px;
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1rem;
    color: var(--color-base-dark);
    flex-shrink: 0;
  }

  .author-body {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-sm);
  }

  .author-name {
    font-family: var(--font-display);
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
  }

  .author-links {
    display: flex;
    flex-direction: column;
    gap: 2px;
  }

  .author-link {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.7;
  }

  /* Final quote */
  .final-quote {
    display: flex;
    gap: var(--spacing-md);
    align-items: flex-start;
    padding: var(--spacing-md) var(--spacing-lg);
    background: rgba(59, 130, 246, 0.06);
    border: 1px dashed rgba(96, 165, 250, 0.2);
    border-radius: var(--radius-sm);
  }

  .quote-icon { font-size: 1.1rem; flex-shrink: 0; margin-top: 2px; }

  .final-quote p {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.65;
    margin-bottom: 0;
    font-style: italic;
  }

  /* Orbs */
  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(100px);
    pointer-events: none;
    z-index: 0;
  }

  .orb-1 {
    width: 400px;
    height: 400px;
    background: rgba(59, 130, 246, 0.07);
    top: -80px;
    right: -80px;
    animation: floatOrb 14s ease-in-out infinite;
  }

  .orb-2 {
    width: 300px;
    height: 300px;
    background: rgba(96, 165, 250, 0.05);
    bottom: -60px;
    left: 50px;
    animation: floatOrb 10s ease-in-out infinite reverse;
  }

  @keyframes moveGrid {
    0%   { transform: translate(0, 0); }
    100% { transform: translate(60px, 60px); }
  }

  @keyframes floatOrb {
    0%, 100% { transform: translateY(0); }
    50%       { transform: translateY(-25px); }
  }

  @media (max-width: 900px) {
    .main-layout { grid-template-columns: 1fr; }
  }
</style>
