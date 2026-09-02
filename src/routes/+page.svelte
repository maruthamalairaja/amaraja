<svelte:head>
  <title>amaraja.in — Launching Soon</title>
  <meta name="description" content="amaraja.in is launching soon. Stay tuned for something amazing." />
  <link rel="preconnect" href="https://fonts.googleapis.com" />
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@300;400;600;700&family=Outfit:wght@300;400;500;600;700&display=swap" rel="stylesheet" />
</svelte:head>

<div class="scene">
  <!-- Ambient floating particles -->
  {#each Array(20) as _, i}
    <div
      class="particle"
      style="
        --x: {Math.random() * 100}%;
        --y: {Math.random() * 100}%;
        --size: {1 + Math.random() * 3}px;
        --duration: {4 + Math.random() * 8}s;
        --delay: {Math.random() * 6}s;
        --drift: {-30 + Math.random() * 60}px;
      "
    ></div>
  {/each}

  <!-- Central glow strip -->
  <div class="glow-strip"></div>

  <!-- Content -->
  <div class="content">
    <!-- Pulsing radar / concentric rings -->
    <div class="radar">
      <div class="ring ring-1"></div>
      <div class="ring ring-2"></div>
      <div class="ring ring-3"></div>
      <div class="dot"></div>
    </div>

    <h1 class="brand">amaraja.in</h1>
    <p class="tagline">LAUNCHING SOON</p>

    <!-- Subtle divider -->
    <div class="divider"></div>

    <p class="sub-text">Something amazing is on the way.</p>
  </div>

  <!-- Bottom ambient light -->
  <div class="bottom-glow"></div>
</div>

<style>
  /* ── Reset & Base ──────────────────────────────── */
  :global(*) {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  :global(html, body) {
    height: 100%;
    overflow: hidden;
    background: #1a0a06;
    font-family: 'Outfit', 'Inter', system-ui, sans-serif;
  }

  /* ── Scene ─────────────────────────────────────── */
  .scene {
    position: relative;
    width: 100vw;
    height: 100vh;
    display: flex;
    align-items: center;
    justify-content: center;
    background:
      radial-gradient(ellipse at 50% 40%, rgba(120, 30, 10, 0.35) 0%, transparent 60%),
      radial-gradient(ellipse at 20% 50%, rgba(80, 20, 5, 0.25) 0%, transparent 50%),
      radial-gradient(ellipse at 80% 60%, rgba(90, 35, 10, 0.2) 0%, transparent 50%),
      linear-gradient(180deg, #1a0a06 0%, #2a0f08 40%, #1a0a06 100%);
    overflow: hidden;
  }

  /* ── Central Glow Strip ────────────────────────── */
  .glow-strip {
    position: absolute;
    top: 0;
    left: 50%;
    transform: translateX(-50%);
    width: 280px;
    height: 100%;
    background: linear-gradient(
      180deg,
      rgba(60, 18, 8, 0.0) 0%,
      rgba(80, 25, 10, 0.3) 20%,
      rgba(100, 35, 12, 0.35) 50%,
      rgba(80, 25, 10, 0.3) 80%,
      rgba(60, 18, 8, 0.0) 100%
    );
    filter: blur(30px);
    pointer-events: none;
  }

  /* ── Floating Particles ────────────────────────── */
  .particle {
    position: absolute;
    left: var(--x);
    top: var(--y);
    width: var(--size);
    height: var(--size);
    background: radial-gradient(circle, rgba(255, 120, 50, 0.7), transparent);
    border-radius: 50%;
    animation: float var(--duration) ease-in-out var(--delay) infinite;
    pointer-events: none;
    opacity: 0;
  }

  @keyframes float {
    0% {
      opacity: 0;
      transform: translateY(0) translateX(0);
    }
    20% {
      opacity: 0.6;
    }
    80% {
      opacity: 0.4;
    }
    100% {
      opacity: 0;
      transform: translateY(-60px) translateX(var(--drift));
    }
  }

  /* ── Content Container ─────────────────────────── */
  .content {
    position: relative;
    z-index: 2;
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 6px;
    animation: fadeUp 1.6s ease-out;
  }

  @keyframes fadeUp {
    0% {
      opacity: 0;
      transform: translateY(30px);
    }
    100% {
      opacity: 1;
      transform: translateY(0);
    }
  }

  /* ── Radar / Concentric Rings ──────────────────── */
  .radar {
    position: relative;
    width: 90px;
    height: 90px;
    margin-bottom: 24px;
    display: flex;
    align-items: center;
    justify-content: center;
  }

  .ring {
    position: absolute;
    border-radius: 50%;
    border: 1px solid rgba(230, 90, 30, 0.25);
  }

  .ring-1 {
    width: 90px;
    height: 90px;
    border-color: rgba(230, 90, 30, 0.12);
    animation: pulseRing 3s ease-out infinite;
  }

  .ring-2 {
    width: 60px;
    height: 60px;
    border-color: rgba(230, 90, 30, 0.2);
    animation: pulseRing 3s ease-out 0.6s infinite;
  }

  .ring-3 {
    width: 34px;
    height: 34px;
    border-color: rgba(230, 90, 30, 0.35);
    animation: pulseRing 3s ease-out 1.2s infinite;
  }

  .dot {
    position: relative;
    width: 10px;
    height: 10px;
    background: #e8551a;
    border-radius: 50%;
    box-shadow:
      0 0 12px 3px rgba(232, 85, 26, 0.6),
      0 0 30px 8px rgba(232, 85, 26, 0.2);
    animation: glowPulse 2s ease-in-out infinite;
  }

  @keyframes pulseRing {
    0% {
      transform: scale(0.85);
      opacity: 0.6;
    }
    50% {
      transform: scale(1.1);
      opacity: 0.2;
    }
    100% {
      transform: scale(0.85);
      opacity: 0.6;
    }
  }

  @keyframes glowPulse {
    0%, 100% {
      box-shadow:
        0 0 12px 3px rgba(232, 85, 26, 0.6),
        0 0 30px 8px rgba(232, 85, 26, 0.2);
    }
    50% {
      box-shadow:
        0 0 18px 6px rgba(232, 85, 26, 0.8),
        0 0 50px 14px rgba(232, 85, 26, 0.3);
    }
  }

  /* ── Typography ────────────────────────────────── */
  .brand {
    font-family: 'Outfit', sans-serif;
    font-size: 2.6rem;
    font-weight: 700;
    color: #f0ddd2;
    letter-spacing: 1px;
    text-shadow: 0 0 40px rgba(232, 85, 26, 0.25);
    line-height: 1.1;
  }

  .tagline {
    font-family: 'Inter', sans-serif;
    font-size: 0.85rem;
    font-weight: 400;
    color: #d4734a;
    letter-spacing: 5px;
    text-transform: uppercase;
    margin-top: 6px;
  }

  .divider {
    width: 40px;
    height: 1px;
    background: linear-gradient(90deg, transparent, rgba(232, 85, 26, 0.5), transparent);
    margin: 22px 0 14px;
  }

  .sub-text {
    font-family: 'Inter', sans-serif;
    font-size: 0.82rem;
    font-weight: 300;
    color: rgba(210, 170, 145, 0.55);
    letter-spacing: 1.5px;
  }

  /* ── Bottom Ambient Glow ───────────────────────── */
  .bottom-glow {
    position: absolute;
    bottom: -60px;
    left: 50%;
    transform: translateX(-50%);
    width: 500px;
    height: 180px;
    background: radial-gradient(ellipse, rgba(180, 70, 20, 0.15) 0%, transparent 70%);
    pointer-events: none;
  }

  /* ── Responsive ────────────────────────────────── */
  @media (max-width: 600px) {
    .brand {
      font-size: 2rem;
    }

    .tagline {
      font-size: 0.72rem;
      letter-spacing: 4px;
    }

    .sub-text {
      font-size: 0.72rem;
    }

    .radar {
      width: 70px;
      height: 70px;
      margin-bottom: 18px;
    }

    .ring-1 {
      width: 70px;
      height: 70px;
    }

    .ring-2 {
      width: 46px;
      height: 46px;
    }

    .ring-3 {
      width: 26px;
      height: 26px;
    }

    .glow-strip {
      width: 200px;
    }
  }
</style>
