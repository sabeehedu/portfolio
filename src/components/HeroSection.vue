<script setup lang="ts">
function scrollToProjects() {
  document.getElementById('projects')?.scrollIntoView({ behavior: 'smooth' })
}
function scrollToContact() {
  document.getElementById('contact')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section id="hero" class="hero">
    <div class="hero-bg-text">PORTFOLIO</div>
    <div class="hero-inner">
      <div class="hero-badge reveal">Available for work · 2025</div>
      <h1 class="hero-title reveal reveal-delay-1">
        Crafting digital<br />
        <em>experiences</em><br />
        that matter.
      </h1>
      <p class="hero-sub reveal reveal-delay-2">
        I'm Alex — a full-stack developer &amp; designer based in London.<br />
        I build thoughtful products at the intersection of code and design.
      </p>
      <div class="hero-actions reveal reveal-delay-3">
        <button class="btn-primary" @click="scrollToProjects">View my work</button>
        <button class="btn-secondary" @click="scrollToContact">Get in touch</button>
      </div>
      <div class="hero-scroll reveal reveal-delay-4">
        <span>Scroll</span>
        <div class="scroll-line" />
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
  padding: 0 2rem;
}
.hero-bg-text {
  position: absolute;
  bottom: -2vw;
  right: -1vw;
  font-family: var(--font-display);
  font-size: clamp(80px, 18vw, 240px);
  font-weight: 800;
  color: var(--border);
  opacity: 0.35;
  letter-spacing: -0.04em;
  pointer-events: none;
  user-select: none;
  line-height: 1;
}
.hero-inner {
  max-width: 1100px;
  margin: 0 auto;
  width: 100%;
  padding-top: 80px;
}
.hero-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.8125rem;
  color: var(--accent);
  border: 1px solid var(--accent);
  padding: 0.375rem 0.875rem;
  border-radius: 100px;
  margin-bottom: 2rem;
  font-weight: 500;
  letter-spacing: 0.02em;
}
.hero-badge::before {
  content: '';
  width: 6px; height: 6px;
  background: var(--accent);
  border-radius: 50%;
  animation: pulse 2s infinite;
}
@keyframes pulse {
  0%, 100% { opacity: 1; }
  50% { opacity: 0.3; }
}
.hero-title {
  font-family: var(--font-display);
  font-size: clamp(2.8rem, 7vw, 5.5rem);
  font-weight: 800;
  line-height: 1.05;
  letter-spacing: -0.03em;
  color: var(--fg);
  margin-bottom: 1.75rem;
}
.hero-title em {
  font-style: italic;
  color: var(--accent);
  font-weight: 700;
}
.hero-sub {
  font-size: clamp(1rem, 1.5vw, 1.125rem);
  color: var(--fg-muted);
  line-height: 1.75;
  max-width: 520px;
  margin-bottom: 2.5rem;
  font-weight: 300;
}
.hero-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}
.btn-primary {
  background: var(--fg);
  color: var(--bg);
  border: none;
  padding: 0.875rem 1.75rem;
  border-radius: 10px;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  font-weight: 500;
  cursor: pointer;
  transition: background 0.2s, transform 0.2s, opacity 0.2s;
  letter-spacing: 0.01em;
}
.btn-primary:hover { opacity: 0.85; transform: translateY(-1px); }

.btn-secondary {
  background: transparent;
  color: var(--fg);
  border: 1px solid var(--border);
  padding: 0.875rem 1.75rem;
  border-radius: 10px;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  font-weight: 500;
  cursor: pointer;
  transition: border-color 0.2s, background 0.2s, transform 0.2s;
}
.btn-secondary:hover { border-color: var(--fg-muted); background: var(--bg-secondary); transform: translateY(-1px); }

.hero-scroll {
  position: absolute;
  bottom: 2.5rem;
  left: 2rem;
  display: flex;
  align-items: center;
  gap: 1rem;
  font-size: 0.75rem;
  color: var(--fg-muted);
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
.scroll-line {
  width: 40px;
  height: 1px;
  background: var(--fg-muted);
  position: relative;
  overflow: hidden;
}
.scroll-line::after {
  content: '';
  position: absolute;
  top: 0; left: -100%;
  width: 100%; height: 100%;
  background: var(--accent);
  animation: scanline 2s infinite;
}
@keyframes scanline {
  to { left: 100%; }
}

@media (max-width: 640px) {
  .hero-scroll { display: none; }
}
</style>
