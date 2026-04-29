<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const isDark = ref(false)
const scrolled = ref(false)
const menuOpen = ref(false)

function toggleTheme() {
  isDark.value = !isDark.value
  document.documentElement.setAttribute('data-theme', isDark.value ? 'dark' : '')
}

function handleScroll() {
  scrolled.value = window.scrollY > 40
}

function scrollTo(id: string) {
  menuOpen.value = false
  document.getElementById(id)?.scrollIntoView({ behavior: 'smooth' })
}

onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))
</script>

<template>
  <nav :class="['navbar', { scrolled }]">
    <div class="nav-inner">
      <a class="nav-logo" href="#hero" @click.prevent="scrollTo('hero')">
        <span class="logo-dot" />Sabeeh<span class="accent">.</span>
      </a>

      <div class="nav-links desktop">
        <button @click="scrollTo('about')">About</button>
        <button @click="scrollTo('projects')">Work</button>
        <button @click="scrollTo('skills')">Skills</button>
        <button @click="scrollTo('contact')">Contact</button>
      </div>

      <div class="nav-actions">
        <button class="theme-toggle" @click="toggleTheme" :aria-label="isDark ? 'Light mode' : 'Dark mode'">
          <svg v-if="!isDark" width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <circle cx="12" cy="12" r="5"/><line x1="12" y1="1" x2="12" y2="3"/><line x1="12" y1="21" x2="12" y2="23"/>
            <line x1="4.22" y1="4.22" x2="5.64" y2="5.64"/><line x1="18.36" y1="18.36" x2="19.78" y2="19.78"/>
            <line x1="1" y1="12" x2="3" y2="12"/><line x1="21" y1="12" x2="23" y2="12"/>
            <line x1="4.22" y1="19.78" x2="5.64" y2="18.36"/><line x1="18.36" y1="5.64" x2="19.78" y2="4.22"/>
          </svg>
          <svg v-else width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
            <path d="M21 12.79A9 9 0 1 1 11.21 3 7 7 0 0 0 21 12.79z"/>
          </svg>
        </button>
        <button class="hamburger" @click="menuOpen = !menuOpen" aria-label="Menu">
          <span :class="{ open: menuOpen }" />
          <span :class="{ open: menuOpen }" />
        </button>
      </div>
    </div>

    <div :class="['mobile-menu', { open: menuOpen }]">
      <button @click="scrollTo('about')">About</button>
      <button @click="scrollTo('projects')">Work</button>
      <button @click="scrollTo('skills')">Skills</button>
      <button @click="scrollTo('contact')">Contact</button>
    </div>
  </nav>
</template>

<style scoped>
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 100;
  background: var(--nav-bg);
  backdrop-filter: blur(16px);
  -webkit-backdrop-filter: blur(16px);
  border-bottom: 1px solid transparent;
  transition: border-color 0.3s, box-shadow 0.3s;
}
.navbar.scrolled {
  border-color: var(--border);
  box-shadow: 0 1px 24px rgba(0,0,0,0.06);
}
.nav-inner {
  max-width: 1100px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 64px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.nav-logo {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--fg);
  text-decoration: none;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}
.logo-dot {
  width: 8px; height: 8px;
  background: var(--accent);
  border-radius: 50%;
  display: inline-block;
}
.accent { color: var(--accent); }

.nav-links.desktop {
  display: flex;
  gap: 0.25rem;
}
.nav-links.desktop button {
  background: none;
  border: none;
  cursor: pointer;
  font-family: var(--font-body);
  font-size: 0.875rem;
  color: var(--fg-muted);
  padding: 0.5rem 0.875rem;
  border-radius: 6px;
  transition: color 0.2s, background 0.2s;
  letter-spacing: 0.01em;
}
.nav-links.desktop button:hover {
  color: var(--fg);
  background: var(--bg-secondary);
}
.nav-actions {
  display: flex;
  align-items: center;
  gap: 0.5rem;
}
.theme-toggle {
  background: none;
  border: 1px solid var(--border);
  border-radius: 8px;
  width: 36px; height: 36px;
  display: flex; align-items: center; justify-content: center;
  cursor: pointer;
  color: var(--fg-muted);
  transition: color 0.2s, border-color 0.2s, background 0.2s;
}
.theme-toggle:hover { color: var(--fg); border-color: var(--fg-muted); }

.hamburger {
  display: none;
  flex-direction: column;
  gap: 5px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 6px;
}
.hamburger span {
  display: block;
  width: 22px; height: 2px;
  background: var(--fg);
  border-radius: 2px;
  transition: transform 0.3s, opacity 0.3s;
  transform-origin: center;
}
.hamburger span.open:first-child { transform: translateY(7px) rotate(45deg); }
.hamburger span.open:last-child { transform: translateY(-7px) rotate(-45deg); }

.mobile-menu {
  display: none;
  flex-direction: column;
  padding: 0 2rem 1rem;
  gap: 0.25rem;
  overflow: hidden;
  max-height: 0;
  transition: max-height 0.4s var(--ease-out-expo);
}
.mobile-menu.open { max-height: 300px; }
.mobile-menu button {
  background: none; border: none;
  text-align: left;
  font-family: var(--font-body);
  font-size: 1rem;
  color: var(--fg-muted);
  padding: 0.625rem 0;
  cursor: pointer;
  border-bottom: 1px solid var(--border);
  transition: color 0.2s;
}
.mobile-menu button:hover { color: var(--fg); }

@media (max-width: 640px) {
  .nav-links.desktop { display: none; }
  .hamburger { display: flex; }
  .mobile-menu { display: flex; }
}
</style>
