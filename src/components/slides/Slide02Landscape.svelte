<script lang="ts">
  import { onMount } from 'svelte';
  import { animateSlideEntrance } from '@/utils/animations';
  let slideElement: HTMLElement;
  onMount(() => { animateSlideEntrance(slideElement); });

  const tools = [
    {
      name: 'GitHub Copilot',
      category: 'IDE Plugin',
      desc: 'El pionero. Autocompletado + chat. Integrado en VS Code, JetBrains.',
      strength: 'Completions',
      color: '#6d28d9',
      icon: '🐙',
      badge: 'Microsoft',
    },
    {
      name: 'Cursor',
      category: 'IDE Propio',
      desc: 'Fork de VS Code con agente nativo. Composer para cambios multi-archivo.',
      strength: 'Multi-file edits',
      color: '#0ea5e9',
      icon: '⚡',
      badge: 'Popular',
    },
    {
      name: 'Antigravity',
      category: 'IDE Propio',
      desc: 'IDE de Google con Gemini integrado. Surge de la adquisición de Windsurf.',
      strength: 'Gemini nativo',
      color: '#ea4335',
      icon: '🚀',
      badge: 'Google',
    },
    {
      name: 'OpenCode',
      category: 'CLI / Terminal',
      desc: 'Open source. Terminal-first. Multi-modelo. Sin lock-in a ningún proveedor.',
      strength: 'Open Source',
      color: '#f59e0b',
      icon: '🖥️',
      badge: 'OSS',
      featured: true,
    },
    {
      name: 'Claude Code',
      category: 'CLI / Terminal',
      desc: 'CLI oficial de Anthropic. Agente autónomo con acceso a ficheros, terminal y git.',
      strength: 'Autonomía total',
      color: '#3B82F6',
      icon: '🤖',
      badge: 'Anthropic',
    },
    {
      name: 'Codex',
      category: 'CLI / Terminal',
      desc: 'CLI de OpenAI. Open source, construido en Rust. Similar a Claude Code.',
      strength: 'Open Source',
      color: '#10a37f',
      icon: '💻',
      badge: 'OpenAI',
    },
  ];
</script>

<div class="swiper-slide" bind:this={slideElement}>
  <div class="slide-background"></div>

  <div class="slide-content">
    <div class="slide-header">
      <span class="label">El panorama</span>
      <h2 class="title">¿Qué herramientas<br />tenemos disponibles?</h2>
      <p class="subtitle">No todas son iguales. Cada una tiene su filosofía.</p>
    </div>

    <div class="tools-grid">
      {#each tools as tool}
        <div class="tool-card card-glass" class:featured={tool.featured}>
          <div class="tool-header">
            <span class="tool-icon">{tool.icon}</span>
            <div class="tool-meta">
              <span class="tool-name">{tool.name}</span>
              <span class="tool-category">{tool.category}</span>
            </div>
            <span class="tool-badge" style="background: {tool.color}20; border-color: {tool.color}60; color: {tool.color}">
              {tool.badge}
            </span>
          </div>
          <p class="tool-desc">{tool.desc}</p>
          <div class="tool-strength">
            <span class="strength-label">Key feature:</span>
            <span class="strength-value" style="color: {tool.color}">{tool.strength}</span>
          </div>
        </div>
      {/each}
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
      radial-gradient(ellipse at 80% 20%, rgba(59, 130, 246, 0.08) 0%, transparent 50%),
      radial-gradient(ellipse at 10% 80%, rgba(30, 58, 138, 0.12) 0%, transparent 50%);
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
    gap: var(--spacing-2xl);
  }

  .slide-header {
    text-align: center;
  }

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

  .subtitle {
    font-size: 1.1rem;
    color: var(--color-electric);
    opacity: 0.8;
    margin-bottom: 0;
  }

  /* Tools grid */
  .tools-grid {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    gap: var(--spacing-md);
  }

  .tool-card {
    display: flex;
    flex-direction: column;
    gap: var(--spacing-md);
    padding: var(--spacing-xl);
    transition: all var(--transition-base);
    position: relative;
  }

  .tool-card.featured {
    border-color: rgba(59, 130, 246, 0.5);
    background: rgba(30, 58, 138, 0.25);
    box-shadow:
      0 0 30px rgba(59, 130, 246, 0.15),
      0 8px 32px 0 rgba(10, 22, 40, 0.8),
      inset 0 1px 1px 0 rgba(96, 165, 250, 0.15);
  }

  .tool-card.featured::before {
    content: '★ Mi favorito';
    position: absolute;
    top: -12px;
    left: 50%;
    transform: translateX(-50%);
    background: linear-gradient(135deg, var(--color-accent-bright), var(--color-electric));
    color: var(--color-base-dark);
    font-family: var(--font-mono);
    font-size: 0.65rem;
    font-weight: 700;
    padding: 3px 12px;
    border-radius: 999px;
    white-space: nowrap;
  }

  .tool-header {
    display: flex;
    align-items: flex-start;
    gap: var(--spacing-sm);
    flex-wrap: wrap;
  }

  .tool-icon {
    font-size: 1.6rem;
    line-height: 1;
    flex-shrink: 0;
  }

  .tool-meta {
    flex: 1;
    min-width: 0;
  }

  .tool-name {
    display: block;
    font-family: var(--font-display);
    font-size: 1rem;
    font-weight: 700;
    color: var(--color-neutral-light);
    line-height: 1.2;
    margin-bottom: 2px;
  }

  .tool-category {
    display: block;
    font-family: var(--font-mono);
    font-size: 0.7rem;
    color: var(--color-electric);
    opacity: 0.7;
    text-transform: uppercase;
    letter-spacing: 0.08em;
  }

  .tool-badge {
    font-family: var(--font-mono);
    font-size: 0.65rem;
    font-weight: 700;
    padding: 2px 8px;
    border-radius: 999px;
    border: 1px solid;
    white-space: nowrap;
    flex-shrink: 0;
    letter-spacing: 0.05em;
  }

  .tool-desc {
    font-size: 0.85rem;
    color: var(--color-neutral-light);
    opacity: 0.75;
    line-height: 1.55;
    margin-bottom: 0;
    flex: 1;
  }

  .tool-strength {
    display: flex;
    align-items: center;
    gap: var(--spacing-sm);
    padding-top: var(--spacing-sm);
    border-top: 1px solid rgba(96, 165, 250, 0.1);
    font-size: 0.78rem;
  }

  .strength-label {
    color: var(--color-neutral-light);
    opacity: 0.5;
    font-family: var(--font-mono);
  }

  .strength-value {
    font-family: var(--font-mono);
    font-weight: 600;
  }

  @media (max-width: 1100px) {
    .tools-grid { grid-template-columns: repeat(3, 1fr); }
  }

  @media (max-width: 768px) {
    .tools-grid { grid-template-columns: repeat(2, 1fr); }
    .title { font-size: clamp(1.6rem, 5vw, 2.5rem); }
  }

  @media (max-width: 480px) {
    .tools-grid { grid-template-columns: 1fr; }
  }

  @media (max-width: 390px) {
    .slide-content {
      padding: var(--spacing-lg) var(--spacing-md);
    }
    .tool-card {
      padding: var(--spacing-lg);
    }
    .tool-desc {
      font-size: 0.8rem;
    }
  }
</style>
