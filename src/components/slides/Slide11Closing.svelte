<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });



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

      <!-- Quote + Author + Branding -->
      <div class="right-col">
        <div class="final-quote">
          <span class="quote-icon">💬</span>
          <p>"La IA no te va a sustituir.<br />Te va a sustituir alguien que sabe usar la IA mejor que tú."</p>
        </div>
        <div class="author-final card-glass">
          <img src="https://www.gravatar.com/avatar/8461e0b8674185c1df153079e820504b?s=96&d=mp" alt="Alejandro de la Fuente" class="author-avatar" />
          <div class="author-body">
            <span class="author-name">Alejandro de la Fuente</span>
            <div class="author-links">
              <a href="https://tellmealex.dev" target="_blank" rel="noopener noreferrer" class="author-link">🌐 tellmealex.dev</a>
              <a href="https://github.com/TellMeAlex" target="_blank" rel="noopener noreferrer" class="author-link">🐙 github.com/TellMeAlex</a>
              <a href="https://es.linkedin.com/in/alejandro-de-la-fuente" target="_blank" rel="noopener noreferrer" class="author-link">💼 LinkedIn</a>
            </div>
          </div>
        </div>
        <div class="branding">
          Hecho con ❤️ por Código Sin Siesta
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
    grid-template-columns: 1fr 1fr;
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
    gap: var(--spacing-lg);
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
    border-radius: 50%;
    flex-shrink: 0;
    object-fit: cover;
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
    gap: 6px;
  }

  .author-link {
    font-family: var(--font-mono);
    font-size: 0.72rem;
    color: var(--color-electric);
    opacity: 0.7;
    text-decoration: none;
    transition: opacity var(--transition-fast);
  }

  .author-link:hover {
    opacity: 1;
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

  /* Branding */
  .branding {
    text-align: center;
    font-family: var(--font-mono);
    font-size: 0.75rem;
    color: var(--color-electric);
    opacity: 0.6;
    padding-top: var(--spacing-sm);
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

  /* Mobile: Small tablet / large phone */
  @media (max-width: 768px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
      gap: var(--spacing-lg);
    }

    .title {
      font-size: clamp(1.6rem, 5vw, 2.4rem);
    }

    .question {
      font-size: clamp(1.2rem, 4vw, 1.8rem);
    }

    .main-layout {
      gap: var(--spacing-lg);
    }

    .col-title {
      font-size: 0.7rem;
      margin-bottom: var(--spacing-md);
    }

    .takeaway {
      padding: var(--spacing-md);
      gap: var(--spacing-md);
      min-height: 44px;
      align-items: center;
    }

    .ta-num {
      min-width: 44px;
      min-height: 44px;
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top: 0;
    }

    .ta-text {
      font-size: 0.82rem;
    }


    .author-final {
      padding: var(--spacing-md) var(--spacing-lg);
      gap: var(--spacing-md);
    }

    .author-avatar {
      width: 44px;
      height: 44px;
      font-size: 0.9rem;
    }

    .author-name {
      font-size: 0.95rem;
    }

    .author-link {
      font-size: 0.7rem;
    }

    .final-quote {
      padding: var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .final-quote p {
      font-size: 0.8rem;
    }

    .branding {
      font-size: 0.7rem;
    }
  }

  /* Mobile: Phone */
  @media (max-width: 480px) {
    .slide-content {
      padding: var(--spacing-md) var(--spacing-sm);
      gap: var(--spacing-md);
    }

    .closing-header {
      margin-bottom: var(--spacing-sm);
    }

    .title {
      font-size: clamp(1.4rem, 6vw, 1.8rem);
    }

    .question {
      font-size: clamp(1rem, 5vw, 1.4rem);
    }

    .col-title {
      font-size: 0.65rem;
      margin-bottom: var(--spacing-sm);
    }

    .takeaways-list {
      gap: var(--spacing-sm);
    }

    .takeaway {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
      min-height: 44px;
    }

    .ta-num {
      min-width: 44px;
      font-size: 0.65rem;
    }

    .ta-text {
      font-size: 0.78rem;
    }


    .author-final {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
    }

    .author-avatar {
      width: 40px;
      height: 40px;
      font-size: 0.85rem;
    }

    .author-name {
      font-size: 0.9rem;
    }

    .author-link {
      font-size: 0.68rem;
    }

    .final-quote {
      padding: var(--spacing-sm) var(--spacing-md);
    }

    .quote-icon {
      font-size: 1rem;
    }

    .final-quote p {
      font-size: 0.75rem;
    }

    .branding {
      font-size: 0.65rem;
      padding-top: var(--spacing-xs);
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

    .question {
      font-size: clamp(0.9rem, 5vw, 1.2rem);
    }

    .col-title {
      font-size: 0.6rem;
    }

    .takeaways-list {
      gap: var(--spacing-xs);
    }

    .takeaway {
      padding: var(--spacing-sm);
      min-height: 44px;
    }

    .ta-num {
      min-width: 44px;
      font-size: 0.6rem;
    }

    .ta-text {
      font-size: 0.72rem;
    }


    .author-final {
      padding: var(--spacing-sm);
    }

    .author-avatar {
      width: 36px;
      height: 36px;
      font-size: 0.8rem;
    }

    .author-name {
      font-size: 0.85rem;
    }

    .author-link {
      font-size: 0.65rem;
    }

    .final-quote {
      padding: var(--spacing-sm);
    }

    .quote-icon {
      font-size: 0.9rem;
    }

    .final-quote p {
      font-size: 0.7rem;
    }

    .branding {
      font-size: 0.6rem;
    }
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

    .question {
      font-size: clamp(1.2rem, 3vw, 1.8rem);
    }

    .main-layout {
      gap: var(--spacing-sm);
    }

    .takeaways-list {
      gap: var(--spacing-sm);
    }

    .takeaway {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-md);
    }

    .right-col {
      gap: var(--spacing-sm);
    }


    .author-final {
      padding: var(--spacing-md);
      gap: var(--spacing-md);
    }

    .final-quote {
      padding: var(--spacing-sm) var(--spacing-md);
      gap: var(--spacing-sm);
    }
  }
</style>
