<script setup lang="ts">
import { ref, reactive } from 'vue'

const form = reactive({ name: '', email: '', message: '' })
const submitted = ref(false)
const loading = ref(false)

async function handleSubmit() {
  if (!form.name || !form.email || !form.message) return
  loading.value = true
  await new Promise(r => setTimeout(r, 1000))
  loading.value = false
  submitted.value = true
}
</script>

<template>
  <section id="contact" class="contact section">
    <div class="container">
      <div class="contact-grid">
        <div class="contact-left">
          <div class="section-label reveal">Contact</div>
          <h2 class="section-title reveal reveal-delay-1">
            Let's build<br />something great.
          </h2>
          <p class="contact-sub reveal reveal-delay-2">
            Have a project in mind or just want to say hello?
            I'm always open to interesting conversations.
          </p>
          <div class="contact-info reveal reveal-delay-3">
            <a href="mailto:sabeehedu@gmail.com" class="contact-email">
              sabeehedu@gmail.com
            </a>
            <div class="social-links">
              <a href="https://github.com/sabeehedu" target="_blank" rel="noopener">GitHub</a>
              <!-- <a href="https://twitter.com/sabeeh" target="_blank" rel="noopener">Twitter</a> -->
              <a href="https://linkedin.com/in/sabeeh-sheikh-318aa1214" target="_blank" rel="noopener">LinkedIn</a>
            </div>
          </div>
        </div>
        <div class="contact-right reveal reveal-delay-2">
          <div v-if="submitted" class="success-msg">
            <div class="success-icon">✓</div>
            <h3>Message sent!</h3>
            <p>Thanks for reaching out. I'll get back to you within 24 hours.</p>
          </div>
          <form v-else @submit.prevent="handleSubmit" class="contact-form" novalidate>
            <div class="field">
              <label for="name">Name</label>
              <input id="name" v-model="form.name" type="text" placeholder="Your name" required />
            </div>
            <div class="field">
              <label for="email">Email</label>
              <input id="email" v-model="form.email" type="email" placeholder="your@email.com" required />
            </div>
            <div class="field">
              <label for="message">Message</label>
              <textarea id="message" v-model="form.message" rows="5" placeholder="Tell me about your project..." required />
            </div>
            <button type="submit" class="btn-submit" :disabled="loading">
              <span v-if="loading">Sending…</span>
              <span v-else>Send message →</span>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
  <footer class="footer">
    <div class="container footer-inner">
      <span>© 2025 Sabeeh. Built with Vue 3 + TypeScript.</span>
      <span>Deployed on Vercel.</span>
    </div>
  </footer>
</template>

<style scoped>
.contact {
  padding: 8rem 2rem 0;
}
.container {
  max-width: 1100px;
  margin: 0 auto;
}
.contact-grid {
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
  letter-spacing: -0.02em;
  line-height: 1.1;
  margin-bottom: 1.5rem;
}
.contact-sub {
  font-size: 1.0625rem;
  color: var(--fg-muted);
  line-height: 1.8;
  font-weight: 300;
  margin-bottom: 2.5rem;
}
.contact-info { display: flex; flex-direction: column; gap: 1.25rem; }
.contact-email {
  font-family: var(--font-display);
  font-size: 1.125rem;
  font-weight: 600;
  color: var(--fg);
  text-decoration: none;
  border-bottom: 2px solid var(--accent);
  padding-bottom: 2px;
  display: inline-block;
  width: fit-content;
  transition: color 0.2s;
}
.contact-email:hover { color: var(--accent); }
.social-links { display: flex; gap: 1.5rem; }
.social-links a {
  font-size: 0.9rem;
  color: var(--fg-muted);
  text-decoration: none;
  font-weight: 500;
  transition: color 0.2s;
}
.social-links a:hover { color: var(--fg); }

/* Form */
.contact-form { display: flex; flex-direction: column; gap: 1.25rem; }
.field { display: flex; flex-direction: column; gap: 0.5rem; }
.field label {
  font-size: 0.8125rem;
  font-weight: 600;
  color: var(--fg-muted);
  letter-spacing: 0.04em;
  text-transform: uppercase;
}
.field input,
.field textarea {
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 10px;
  padding: 0.875rem 1rem;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  color: var(--fg);
  outline: none;
  transition: border-color 0.2s, box-shadow 0.2s;
  resize: none;
}
.field input::placeholder,
.field textarea::placeholder { color: var(--fg-muted); opacity: 0.6; }
.field input:focus,
.field textarea:focus {
  border-color: var(--accent);
  box-shadow: 0 0 0 3px rgba(200,96,42,0.12);
}
.btn-submit {
  background: var(--accent);
  color: white;
  border: none;
  padding: 1rem 1.75rem;
  border-radius: 10px;
  font-family: var(--font-body);
  font-size: 0.9375rem;
  font-weight: 500;
  cursor: pointer;
  transition: opacity 0.2s, transform 0.2s;
  align-self: flex-start;
  letter-spacing: 0.01em;
}
.btn-submit:hover:not(:disabled) { opacity: 0.88; transform: translateY(-1px); }
.btn-submit:disabled { opacity: 0.6; cursor: not-allowed; }

/* Success */
.success-msg {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  gap: 0.75rem;
  padding: 2.5rem;
  background: var(--bg-secondary);
  border: 1px solid var(--border);
  border-radius: 16px;
}
.success-icon {
  width: 48px; height: 48px;
  background: var(--accent);
  color: white;
  border-radius: 50%;
  display: flex; align-items: center; justify-content: center;
  font-size: 1.25rem;
  font-weight: 700;
}
.success-msg h3 {
  font-family: var(--font-display);
  font-size: 1.25rem;
  font-weight: 700;
}
.success-msg p { color: var(--fg-muted); font-size: 0.9375rem; }

/* Footer */
.footer {
  margin-top: 6rem;
  border-top: 1px solid var(--border);
  padding: 2rem;
}
.footer-inner {
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  font-size: 0.8125rem;
  color: var(--fg-muted);
}

@media (max-width: 768px) {
  .contact-grid { grid-template-columns: 1fr; gap: 3rem; }
}
</style>
