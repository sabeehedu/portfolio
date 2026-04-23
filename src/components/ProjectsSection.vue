<script setup lang="ts">
import type { Project } from '../types'

const projects: Project[] = [
  {
    id: 1,
    title: 'Lumino Design System',
    description: 'A comprehensive design system with 80+ accessible components, built for enterprise-scale Vue applications.',
    tags: ['Vue 3', 'TypeScript', 'Storybook', 'WCAG'],
    year: '2024',
    link: 'https://github.com',
  },
  {
    id: 2,
    title: 'Orbit Analytics',
    description: 'Real-time data dashboard for SaaS businesses. Visualizes churn, MRR, and cohort retention with live charts.',
    tags: ['Vue', 'D3.js', 'Node.js', 'PostgreSQL'],
    year: '2024',
    link: 'https://github.com',
  },
  {
    id: 3,
    title: 'Forma CMS',
    description: 'A headless content management system with a block-based editor, versioning, and multi-tenant support.',
    tags: ['TypeScript', 'Express', 'React', 'MongoDB'],
    year: '2023',
    link: 'https://github.com',
  },
  {
    id: 4,
    title: 'Wayfarer App',
    description: 'Travel planning app that generates smart itineraries using AI. Helped 10k+ users plan their trips.',
    tags: ['Vue', 'OpenAI API', 'Supabase', 'Tailwind'],
    year: '2023',
    link: 'https://github.com',
  },
  {
    id: 5,
    title: 'Glyph Type Foundry',
    description: 'E-commerce platform for a boutique type foundry. Includes license management and font preview tools.',
    tags: ['Nuxt 3', 'Stripe', 'Figma API', 'Vercel'],
    year: '2022',
    link: 'https://github.com',
  },
  {
    id: 6,
    title: 'Pulse Monitoring',
    description: 'Uptime and performance monitoring SaaS. Sends alerts via Slack/email and tracks historical data.',
    tags: ['TypeScript', 'Fastify', 'Redis', 'Cron'],
    year: '2022',
    link: 'https://github.com',
  },
]
</script>

<template>
  <section id="projects" class="projects section">
    <div class="container">
      <div class="section-header">
        <div class="section-label reveal">Selected work</div>
        <h2 class="section-title reveal reveal-delay-1">Projects I've built.</h2>
      </div>

      <div class="projects-grid">
        <article
          v-for="(project, i) in projects"
          :key="project.id"
          :class="['project-card reveal', `reveal-delay-${(i % 3) + 1}`]"
        >
          <div class="project-top">
            <span class="project-year">{{ project.year }}</span>
            <a
              v-if="project.link"
              :href="project.link"
              target="_blank"
              rel="noopener"
              class="project-arrow"
              aria-label="View project"
            >↗</a>
          </div>
          <h3 class="project-title">{{ project.title }}</h3>
          <p class="project-desc">{{ project.description }}</p>
          <div class="project-tags">
            <span v-for="tag in project.tags" :key="tag" class="tag">{{ tag }}</span>
          </div>
        </article>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects {
  padding: 8rem 2rem;
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
.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5px;
  background: var(--border);
  border: 1.5px solid var(--border);
  border-radius: 16px;
  overflow: hidden;
}
.project-card {
  background: var(--card-bg);
  padding: 2rem;
  transition: background 0.2s;
  cursor: default;
}
.project-card:hover { background: var(--bg-secondary); }
.project-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 1.25rem;
}
.project-year {
  font-size: 0.75rem;
  color: var(--fg-muted);
  letter-spacing: 0.04em;
}
.project-arrow {
  color: var(--fg-muted);
  text-decoration: none;
  font-size: 1.125rem;
  line-height: 1;
  transition: color 0.2s, transform 0.2s;
  display: block;
}
.project-arrow:hover { color: var(--accent); transform: translate(2px, -2px); }
.project-title {
  font-family: var(--font-display);
  font-size: 1.125rem;
  font-weight: 700;
  letter-spacing: -0.01em;
  margin-bottom: 0.75rem;
  line-height: 1.3;
}
.project-desc {
  font-size: 0.9rem;
  color: var(--fg-muted);
  line-height: 1.7;
  margin-bottom: 1.5rem;
  font-weight: 300;
  flex: 1;
}
.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.375rem;
}
.tag {
  font-size: 0.7rem;
  letter-spacing: 0.03em;
  color: var(--fg-muted);
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  padding: 0.2rem 0.6rem;
  border-radius: 100px;
  font-weight: 500;
}

@media (max-width: 900px) {
  .projects-grid { grid-template-columns: repeat(2, 1fr); }
}
@media (max-width: 600px) {
  .projects-grid { grid-template-columns: 1fr; }
}
</style>
