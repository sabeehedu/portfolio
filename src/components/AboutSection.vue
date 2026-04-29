<script setup lang="ts">
const stats = [
  { value: '5+', label: 'Years experience' },
  { value: '40+', label: 'Projects shipped' },
  { value: '18', label: 'Happy clients' },
]
</script>

<template>
  <section id="about" class="about section">
    <div class="container">
      <div class="about-grid">
        <div class="about-left">
          <div class="section-label reveal">About me</div>
          <h2 class="section-title reveal reveal-delay-1">
            Developer &<br />designer at heart.
          </h2>
          <div class="about-stats">
            <div
              v-for="(stat, i) in stats"
              :key="stat.label"
              :class="['stat', `reveal reveal-delay-${i + 2}`]"
            >
              <span class="stat-value">{{ stat.value }}</span>
              <span class="stat-label">{{ stat.label }}</span>
            </div>
          </div>
        </div>
        <div class="about-right reveal reveal-delay-2">
          <p>
            I'm a full-stack developer with a keen eye for design. I specialize in
            building fast, accessible, and beautifully crafted web applications
            using modern technologies like Vue, TypeScript, and Node.js.
          </p>
          <p>
            My process starts with understanding the problem deeply. I believe the
            best digital products emerge at the intersection of thoughtful engineering
            and deliberate design — each decision serving both the user and the business.
          </p>
          <p>
            When I'm not building things, I'm exploring photography, reading about
            type design, or experimenting with generative art.
          </p>
          <div class="about-links">
            <a href="https://github.com/sabeeh" target="_blank" rel="noopener" class="about-link">
              GitHub ↗
            </a>
            <a href="https://linkedin.com/in/sabeeh-sheikh-318aa1214" target="_blank" rel="noopener" class="about-link">
              LinkedIn ↗
            </a>
            <a href="/resume.pdf" download class="about-link">
              Resume ↓
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.about {
  padding: 8rem 2rem;
  background: var(--bg-secondary);
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.about-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 6rem;
  align-items: start;
}
.section-label {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 1.25rem;
}
.section-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  line-height: 1.1;
  letter-spacing: -0.02em;
  margin-bottom: 3rem;
}
.about-stats {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}
.stat {
  display: flex;
  flex-direction: column;
  padding-bottom: 1.5rem;
  border-bottom: 1px solid var(--border);
}
.stat-value {
  font-family: var(--font-display);
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--accent);
  line-height: 1;
  letter-spacing: -0.03em;
}
.stat-label {
  font-size: 0.875rem;
  color: var(--fg-muted);
  margin-top: 0.25rem;
}
.about-right p {
  color: var(--fg-muted);
  line-height: 1.8;
  margin-bottom: 1.25rem;
  font-size: 1.0625rem;
  font-weight: 300;
}
.about-links {
  display: flex;
  gap: 1.5rem;
  margin-top: 2rem;
  flex-wrap: wrap;
}
.about-link {
  font-size: 0.9375rem;
  font-weight: 500;
  color: var(--fg);
  text-decoration: none;
  border-bottom: 1px solid var(--border);
  padding-bottom: 2px;
  transition: color 0.2s, border-color 0.2s;
}
.about-link:hover { color: var(--accent); border-color: var(--accent); }

@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; gap: 3rem; }
}
</style>
