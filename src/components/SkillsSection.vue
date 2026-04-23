<script setup lang="ts">
import type { Skill } from '../types'

const skills: Skill[] = [
  {
    category: 'Frontend',
    items: ['Vue 3', 'TypeScript', 'React', 'Nuxt', 'CSS / Sass', 'Tailwind', 'Vite', 'Webpack'],
  },
  {
    category: 'Backend',
    items: ['Node.js', 'Express', 'Fastify', 'PostgreSQL', 'MongoDB', 'Redis', 'REST APIs', 'GraphQL'],
  },
  {
    category: 'Design & Tools',
    items: ['Figma', 'Storybook', 'Git', 'Docker', 'Vercel', 'AWS', 'CI/CD', 'Vitest'],
  },
]
</script>

<template>
  <section id="skills" class="skills section">
    <div class="container">
      <div class="section-header">
        <div class="section-label reveal">Expertise</div>
        <h2 class="section-title reveal reveal-delay-1">What I work with.</h2>
      </div>

      <div class="skills-grid">
        <div
          v-for="(skill, i) in skills"
          :key="skill.category"
          :class="['skill-group reveal', `reveal-delay-${i + 1}`]"
        >
          <h3 class="skill-category">{{ skill.category }}</h3>
          <div class="skill-items">
            <span v-for="item in skill.items" :key="item" class="skill-item">
              {{ item }}
            </span>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.skills {
  padding: 8rem 2rem;
  background: var(--bg-secondary);
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.section-header {
  margin-bottom: 4rem;
}
.section-label {
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: var(--accent);
  font-weight: 600;
  margin-bottom: 1rem;
}
.section-title {
  font-family: var(--font-display);
  font-size: clamp(2rem, 4vw, 3rem);
  font-weight: 800;
  letter-spacing: -0.02em;
  line-height: 1.1;
}
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 3rem;
}
.skill-group {}
.skill-category {
  font-family: var(--font-display);
  font-size: 0.75rem;
  font-weight: 700;
  text-transform: uppercase;
  letter-spacing: 0.1em;
  color: var(--fg-muted);
  margin-bottom: 1.5rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--border);
}
.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 0.625rem;
}
.skill-item {
  font-size: 0.9rem;
  color: var(--fg);
  background: var(--card-bg);
  border: 1px solid var(--border);
  padding: 0.5rem 1rem;
  border-radius: 8px;
  font-weight: 400;
  transition: background 0.2s, color 0.2s, border-color 0.2s, transform 0.2s;
  cursor: default;
}
.skill-item:hover {
  background: var(--accent);
  color: white;
  border-color: var(--accent);
  transform: translateY(-2px);
}

@media (max-width: 900px) {
  .skills-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .skills-grid { grid-template-columns: 1fr; }
}
</style>
