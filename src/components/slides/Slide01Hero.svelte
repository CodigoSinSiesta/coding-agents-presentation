<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>
  <div class="animated-grid"></div>

  <div class="slide-content">
    <div class="eyebrow">
      <span class="eyebrow-dot"></span>
      <span>Coding con IA · 2025</span>
    </div>

    <h1 class="title">
      Tu nuevo<br />
      <span class="highlight">compañero</span><br />
      de código
    </h1>

    <p class="subtitle">
      Agentes de IA para desarrolladores que<br />
      quieren trabajar más listos, no más duro.
    </p>

    <div class="tools-row">
      <span class="tool-badge">Cursor</span>
      <span class="tool-badge">Windsurf</span>
      <span class="tool-badge">Copilot</span>
      <span class="tool-badge">OpenCode</span>
      <span class="tool-badge highlight-badge">Claude Code</span>
    </div>

    <div class="author-card card-glass">
      <div class="author-avatar">AL</div>
      <div class="author-info">
        <p class="author-name">Alejandro de la Fuente</p>
        <p class="author-role">Technical Leader · NTT Data · GDE</p>
      </div>
    </div>
  </div>

  <!-- Decorative orbs -->
  <div class="orb orb-1"></div>
  <div class="orb orb-2"></div>
  <div class="orb orb-3"></div>
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
      radial-gradient(ellipse at 15% 60%, rgba(59, 130, 246, 0.12) 0%, transparent 55%),
      radial-gradient(ellipse at 85% 30%, rgba(30, 58, 138, 0.18) 0%, transparent 55%);
    z-index: 1;
  }

  .animated-grid {
    position: absolute;
    inset: 0;
    background-image:
      linear-gradient(rgba(96, 165, 250, 0.07) 1px, transparent 1px),
      linear-gradient(90deg, rgba(96, 165, 250, 0.07) 1px, transparent 1px);
    background-size: 60px 60px;
    z-index: 0;
    animation: moveGrid 25s linear infinite;
  }

  .slide-content {
    position: relative;
    z-index: 2;
    max-width: 1100px;
    width: 100%;
    padding: var(--spacing-content);
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    gap: var(--spacing-xl);
  }

  /* Eyebrow */
  .eyebrow {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    font-family: var(--font-mono);
    font-size: 0.85rem;
    color: var(--color-electric);
    letter-spacing: 0.12em;
    text-transform: uppercase;
    animation: fadeUp 0.6s ease-out backwards;
  }

  .eyebrow-dot {
    width: 8px;
    height: 8px;
    background: var(--color-accent-bright);
    border-radius: 50%;
    animation: pulse 2s ease-in-out infinite;
    box-shadow: 0 0 8px rgba(59, 130, 246, 0.8);
  }

  /* Title */
  .title {
    font-size: clamp(3.5rem, 9vw, 7.5rem);
    font-weight: 900;
    line-height: 1.0;
    margin-bottom: 0;
    color: var(--color-neutral-light);
    animation: fadeUp 0.7s ease-out 0.1s backwards;
  }

  .highlight {
    background: linear-gradient(135deg, var(--color-accent-bright) 0%, var(--color-electric) 50%, #a78bfa 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    background-clip: text;
  }

  /* Subtitle */
  .subtitle {
    font-size: clamp(1.1rem, 2.2vw, 1.5rem);
    color: var(--color-neutral-light);
    opacity: 0.75;
    font-family: var(--font-body);
    font-weight: 400;
    line-height: 1.6;
    margin-bottom: 0;
    animation: fadeUp 0.7s ease-out 0.2s backwards;
  }

  /* Tools row */
  .tools-row {
    display: flex;
    flex-wrap: wrap;
    gap: var(--spacing-sm);
    animation: fadeUp 0.7s ease-out 0.3s backwards;
  }

  .tool-badge {
    padding: var(--spacing-xs) var(--spacing-lg);
    font-family: var(--font-mono);
    font-size: 0.8rem;
    font-weight: 600;
    background: rgba(30, 58, 138, 0.4);
    border: 1px solid rgba(96, 165, 250, 0.25);
    border-radius: 999px;
    color: var(--color-electric);
    letter-spacing: 0.05em;
    backdrop-filter: blur(4px);
  }

  .highlight-badge {
    background: rgba(59, 130, 246, 0.2);
    border-color: var(--color-accent-bright);
    color: var(--color-neutral-light);
    box-shadow: 0 0 12px rgba(59, 130, 246, 0.3);
  }

  /* Author card */
  .author-card {
    display: flex;
    align-items: center;
    gap: var(--spacing-lg);
    padding: var(--spacing-lg) var(--spacing-xl);
    animation: fadeUp 0.7s ease-out 0.4s backwards;
  }

  .author-avatar {
    width: 52px;
    height: 52px;
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    border-radius: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-family: var(--font-display);
    font-weight: 800;
    font-size: 1.1rem;
    color: var(--color-base-dark);
    flex-shrink: 0;
  }

  .author-name {
    font-size: 1.1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    margin-bottom: var(--spacing-xs);
  }

  .author-role {
    font-size: 0.9rem;
    color: var(--color-electric);
    opacity: 0.85;
    font-family: var(--font-mono);
  }

  /* Decorative orbs */
  .orb {
    position: absolute;
    border-radius: 50%;
    filter: blur(80px);
    pointer-events: none;
    z-index: 0;
  }

  .orb-1 {
    width: 500px;
    height: 500px;
    background: rgba(59, 130, 246, 0.08);
    top: -100px;
    right: -100px;
    animation: floatOrb 12s ease-in-out infinite;
  }

  .orb-2 {
    width: 300px;
    height: 300px;
    background: rgba(96, 165, 250, 0.06);
    bottom: 50px;
    right: 200px;
    animation: floatOrb 9s ease-in-out infinite reverse;
  }

  .orb-3 {
    width: 200px;
    height: 200px;
    background: rgba(167, 139, 250, 0.05);
    bottom: -50px;
    left: 100px;
    animation: floatOrb 15s ease-in-out infinite;
  }

  @keyframes fadeUp {
    from { opacity: 0; transform: translateY(28px); }
    to   { opacity: 1; transform: translateY(0); }
  }

  @keyframes moveGrid {
    0%   { transform: translate(0, 0); }
    100% { transform: translate(60px, 60px); }
  }

  @keyframes pulse {
    0%, 100% { opacity: 1; transform: scale(1); }
    50%       { opacity: 0.6; transform: scale(0.85); }
  }

  @keyframes floatOrb {
    0%, 100% { transform: translateY(0) scale(1); }
    50%       { transform: translateY(-30px) scale(1.05); }
  }

  @media (max-width: 768px) {
    .title { font-size: clamp(2.8rem, 10vw, 4.5rem); }
    .tools-row { gap: var(--spacing-xs); }
    .author-card { padding: var(--spacing-md) var(--spacing-lg); }
  }

  @media (max-width: 480px) {
    .title { font-size: clamp(2.2rem, 10vw, 3.5rem); }
    .subtitle { font-size: 1rem; }
    .author-avatar { width: 42px; height: 42px; font-size: 0.9rem; }
  }
</style>
