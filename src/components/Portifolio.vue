<template>
  <div class="min-h-screen">

    <!-- ===== NAVBAR ===== -->
    <nav class="navbar" :class="{ 'navbar--scrolled': scrolled }">
      <div class="navbar__inner">
        <button class="navbar__logo" @click="scrollTo('#hero')">&lt;Jonatas /&gt;</button>

        <ul class="navbar__links">
          <li v-for="link in navLinks" :key="link.href">
            <button class="navbar__link" @click="scrollTo(link.href)">{{ link.label }}</button>
          </li>
        </ul>

        <button aria-label="Menu" class="navbar__toggle" @click="mobileOpen = !mobileOpen">
          <span class="bar" :class="{ 'bar--top-open': mobileOpen }" />
          <span class="bar" :class="{ 'bar--mid-open': mobileOpen }" />
          <span class="bar" :class="{ 'bar--bot-open': mobileOpen }" />
        </button>
      </div>

      <transition name="mobile-menu">
        <div v-if="mobileOpen" class="navbar__mobile">
          <ul class="navbar__mobile-list">
            <li v-for="link in navLinks" :key="link.href">
              <button class="navbar__link" @click="scrollTo(link.href)">{{ link.label }}</button>
            </li>
          </ul>
        </div>
      </transition>
    </nav>

    <!-- ===== HERO ===== -->
    <section id="hero" class="hero">
      <div class="blob blob--hero-left" />
      <div class="blob blob--hero-right" />

      <div class="hero__inner">
        <div class="hero__content">
          <div class="hero-anim" style="--hero-delay: 0.1s">
            <span class="badge">Olá, eu sou</span>
          </div>
          <div class="hero-anim" style="--hero-delay: 0.25s">
            <h1 class="hero__name">
              <span class="bracket">&lt; </span>
              <span class="gradient">Jonatas</span>
              <span class="bracket"> /&gt;</span>
            </h1>
          </div>
          <div class="hero-anim" style="--hero-delay: 0.4s">
            <h2 class="hero__role">
              Desenvolvedor <span class="hero__role-hl">Front-End</span>
            </h2>
          </div>
          <div class="hero-anim" style="--hero-delay: 0.55s">
            <p class="hero__bio">
              Sou desenvolvedor Front-End focado em criar interfaces modernas, responsivas e
              bem estruturadas. Gosto de transformar ideias em experiências digitais funcionais
              utilizando JavaScript, Vue.js, HTML e CSS.
            </p>
          </div>
          <div class="hero-anim" style="--hero-delay: 0.7s">
            <div class="hero__cta">
              <button class="btn btn--primary" @click="scrollTo('#projects')">Ver Projetos</button>
              <button class="btn btn--outline" @click="scrollTo('#contact')">Contato</button>
            </div>
          </div>
        </div>

        <div class="hero-anim hero-anim--right" style="--hero-delay: 0.4s">
          <div class="code-card">
            <div class="code-card__pulse-glow" />
            <div class="code-card__window">
              <div class="code-card__bar">
                <span class="dot dot--r" /><span class="dot dot--y" /><span class="dot dot--g" />
                <span class="code-card__file">portfolio.vue</span>
              </div>
              <div class="code-card__body">
                <div><span class="kw">const</span> <span class="vr">dev</span> <span class="mu">=</span> <span class="mu">{</span></div>
                <div class="ind"><span class="pr">nome</span><span class="mu">:</span> <span class="st">'Jonatas'</span><span class="mu">,</span></div>
                <div class="ind"><span class="pr">stack</span><span class="mu">:</span> <span class="mu">[</span><span class="st">'Vue'</span><span class="mu">,</span> <span class="st">'JS'</span><span class="mu">,</span> <span class="st">'CSS'</span><span class="mu">],</span></div>
                <div class="ind"><span class="pr">foco</span><span class="mu">:</span> <span class="st">'Front-End'</span></div>
                <div><span class="mu">};</span></div>
              </div>
            </div>
            <div class="float-icon float-icon--vue">Vue</div>
            <div class="float-icon float-icon--js">JS</div>
            <div class="float-icon float-icon--html">HTML</div>
            <div class="float-icon float-icon--css">CSS</div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== TECNOLOGIAS ===== -->
    <section id="tech" class="section">
      <div class="section__divider" />
      <div class="container">
        <div ref="techHead" :class="['reveal', { 'reveal--visible': techVisible }]">
          <div class="section__head">
            <h2 class="section__title">Principais <span class="gradient">Tecnologias</span></h2>
            <p class="section__sub">Ferramentas e tecnologias que utilizo para construir interfaces incríveis</p>
          </div>
        </div>

        <div class="tech-grid">
          <div
            v-for="(tech, i) in techs"
            :key="tech.name"
            :class="['stagger', { 'stagger--visible': techCardsVisible }]"
            :style="`--i:${i}`"
          >
            <div class="tech-card">
              <div class="tech-card__icon">{{ tech.icon }}</div>
              <h3 class="tech-card__name">{{ tech.name }}</h3>
              <p class="tech-card__desc">{{ tech.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== PROJETOS ===== -->
    <section id="projects" class="section">
      <div class="blob blob--projects" />
      <div class="container">
        <div ref="projHead" :class="['reveal', { 'reveal--visible': projVisible }]">
          <div class="section__head">
            <h2 class="section__title">Meus <span class="gradient">Projetos</span></h2>
            <p class="section__sub">Projetos focados na construção de interfaces modernas e funcionais</p>
          </div>
        </div>

        <div class="proj-grid">
          <div
            v-for="(proj, i) in projects"
            :key="proj.title"
            :class="['stagger', { 'stagger--visible': projCardsVisible }]"
            :style="`--i:${i}`"
          >
            <a class="proj-card" :href="proj.link" rel="noopener noreferrer" target="_blank">
              <div class="proj-card__bar">
                <span class="dot dot--r" /><span class="dot dot--y" /><span class="dot dot--g" />
                <div class="proj-card__url">localhost:3000/{{ slugify(proj.title) }}</div>
              </div>
              <h3 class="proj-card__title">
                {{ proj.title }}
                <svg
                  class="proj-card__ext"
                  fill="none"
                  height="16"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  viewBox="0 0 24 24"
                  width="16"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6" />
                  <polyline points="15 3 21 3 21 9" />
                  <line x1="10" x2="21" y1="14" y2="3" />
                </svg>
              </h3>
              <p class="proj-card__desc">{{ proj.description }}</p>
              <div class="proj-card__tags">
                <span v-for="tag in proj.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
            </a>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== CONTATO ===== -->
    <section id="contact" class="section">
      <div class="blob blob--contact" />
      <div class="container container--narrow">
        <div ref="contHead" :class="['reveal', { 'reveal--visible': contVisible }]" style="text-align:center">
          <h2 class="section__title">Vamos <span class="gradient">Conversar</span>?</h2>
          <p class="section__sub" style="margin-inline:auto">Estou disponível para novos projetos e oportunidades. Entre em contato!</p>
        </div>

        <div ref="contLinks" :class="['reveal', { 'reveal--visible': contLinksVisible }]" style="--delay:0.2s">
          <div class="contact-links">
            <a class="contact-btn" href="mailto:jonatasgomes1090@gmail.com">
              <svg
                fill="none"
                height="20"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                width="20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <rect
                  height="16"
                  rx="2"
                  width="20"
                  x="2"
                  y="4"
                />
                <path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" />
              </svg>
              <span>Email</span>
            </a>
            <a class="contact-btn" href="https://github.com/JonatasGomesss" rel="noopener noreferrer" target="_blank">
              <svg
                fill="none"
                height="20"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                width="20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M15 22v-4a4.8 4.8 0 0 0-1-3.2c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.4 5.4 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65S8.93 17.38 9 18v4" />
                <path d="M9 18c-4.51 2-5-2-7-2" />
              </svg>
              <span>GitHub</span>
            </a>
            <a class="contact-btn" href="https://www.google.com/url?q=https://www.linkedin.com/in/jonatasgomess/" rel="noopener noreferrer" target="_blank">
              <svg
                fill="none"
                height="20"
                stroke="currentColor"
                stroke-linecap="round"
                stroke-linejoin="round"
                stroke-width="2"
                viewBox="0 0 24 24"
                width="20"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z" />
                <rect height="12" width="4" x="2" y="9" />
                <circle cx="4" cy="4" r="2" />
              </svg>
              <span>LinkedIn</span>
            </a>
          </div>
        </div>

        <div ref="contFoot" :class="['reveal', { 'reveal--visible': contFootVisible }]" style="--delay:0.3s">
          <div class="footer">
            <p class="footer__text">
              &lt;<span style="color:var(--primary)">Jonatas</span> /&gt; © {{ year }} — Todos os direitos reservados
            </p>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
  import { onMounted, onUnmounted, ref } from 'vue'

  // ── Dados estáticos ──────────────────────────────────────────────────────────
  const year = new Date().getFullYear()

  const navLinks = [
    { label: 'Início', href: '#hero' },
    { label: 'Tecnologias', href: '#tech' },
    { label: 'Projetos', href: '#projects' },
    { label: 'Contato', href: '#contact' },
  ]

  const techs = [
    { icon: '🟢', name: 'Vue.js', description: 'Framework que escolhi para desenvolver interfaces modernas e reativas.' },
    { icon: '🧱', name: 'HTML', description: 'Linguagem responsável por estruturar todo o conteúdo das páginas web.' },
    { icon: '🎨', name: 'CSS', description: 'Estiliza e organiza o layout das páginas, criando interfaces visuais atraentes.' },
    { icon: '⚡', name: 'JavaScript', description: 'Linguagem responsável pela lógica e interatividade das aplicações web.' },
  ]

  const projects = [
    {
      title: 'Perspectiva',
      description: 'Blog editorial responsivo com dark/light mode, grid de artigos categorizados e seção de newsletter. Dados estáticos com animações de entrada escalonadas.',
      tags: ['Vue 3', 'CSS', 'JavaScript'],
      link: 'https://blog-three-gilt-75.vercel.app/',
    },
    {
      title: 'Tela de Login',
      description: 'Interface de login moderna com validação e design responsivo.',
      tags: ['Vue', 'Vuetify', 'JavaScript'],
      link: 'https://tela-login-beryl.vercel.app/',
    },
    {
      title: 'Filmes e Séries',
      description: 'Catálogo de filmes e séries consumindo API externa com busca e filtros.',
      tags: ['Vue', 'Vuetify', 'API', 'JavaScript'],
      link: 'https://filmes-series-psi.vercel.app/',
    },
    {
      title: 'Viagem de Chihiro',
      description: 'Landing page temática com animações e design imersivo.',
      tags: ['HTML', 'CSS'],
      link: 'https://viagem-de-chihiro-theta.vercel.app/',
    },
    {
      title: 'Jordan Shoes',
      description: 'Site portfolio com design moderno e código limpo.',
      tags: ['Vue', 'CSS', 'JavaScript'],
      link: 'https://jordanshoes-gilt.vercel.app/',
    },
  ]

  // ── Estado reativo ───────────────────────────────────────────────────────────
  const scrolled = ref(false)
  const mobileOpen = ref(false)

  // ── Refs de visibilidade ─────────────────────────────────────────────────────
  const techHead = ref(null)
  const techVisible = ref(false)
  const techCardsVisible = ref(false)

  const projHead = ref(null)
  const projVisible = ref(false)
  const projCardsVisible = ref(false)

  const contHead = ref(null)
  const contVisible = ref(false)
  const contLinks = ref(null)
  const contLinksVisible = ref(false)
  const contFoot = ref(null)
  const contFootVisible = ref(false)

  // ── Métodos ──────────────────────────────────────────────────────────────────
  function slugify (title) {
    return title.toLowerCase().replace(/\s/g, '-')
  }

  function scrollTo (href) {
    mobileOpen.value = false
    document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
  }

  function onScroll () {
    scrolled.value = window.scrollY > 40
  }

  function observeReveal (elRef, visRef, delay = 0) {
    const obs = new IntersectionObserver(([e]) => {
      if (e.isIntersecting) {
        setTimeout(() => {
          visRef.value = true
        }, delay)
        obs.disconnect()
      }
    }, { rootMargin: '-80px' })
    if (elRef.value) obs.observe(elRef.value)
  }

  // ── Lifecycle ────────────────────────────────────────────────────────────────
  onMounted(() => {
    window.addEventListener('scroll', onScroll)

    observeReveal(techHead, techVisible)
    observeReveal(techHead, techCardsVisible, 200)
    observeReveal(projHead, projVisible)
    observeReveal(projHead, projCardsVisible, 200)
    observeReveal(contHead, contVisible)
    observeReveal(contLinks, contLinksVisible)
    observeReveal(contFoot, contFootVisible)
  })

  onUnmounted(() => {
    window.removeEventListener('scroll', onScroll)
  })
</script>

<style>
/* ══════════════════════════════════════════════════
   TOKENS
══════════════════════════════════════════════════ */
#app {
  --primary:            #6d6aff;
  --primary-rgb:        109, 106, 255;
  --accent:             #a78bfa;
  --accent-rgb:         167, 139, 250;
  --bg:                 #0f0f13;
  --bg-rgb:             15, 15, 19;
  --fg:                 #e8e8f0;
  --muted-fg:           #8080a0;
  --card:               #16161e;
  --border:             rgba(255, 255, 255, 0.08);
  --muted-rgb:          128, 128, 160;
}

/* ══════════════════════════════════════════════════
   RESET
══════════════════════════════════════════════════ */
*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: var(--bg);
  color: var(--fg);
  font-family: 'Inter', sans-serif;
}

/* ══════════════════════════════════════════════════
   ANIMATIONS
══════════════════════════════════════════════════ */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(40px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes pulseGlow {
  0%, 100% {
    opacity: 0.5;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1.12);
  }
}

@keyframes float {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(-8px); }
}

@keyframes shimmer {
  0%   { background-position: 0% center; }
  100% { background-position: 220% center; }
}
</style>

<style scoped>
/* ── Layout ── */
.container {
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
}

.container--narrow {
  max-width: 48rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  text-align: center;
}

.section {
  position: relative;
  padding: 8rem 0;
  overflow: hidden;
}

.section__divider {
  position: absolute;
  top: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 1px;
  height: 5rem;
  background: linear-gradient(to bottom, transparent, var(--border));
}

.section__head {
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  flex-direction: column;
  margin-bottom: 4rem;
}

.section__title {
  font-size: clamp(1.75rem, 4vw, 2.25rem);
  font-weight: 700;
  margin-top: 0.75rem;
}

.section__sub {
  color: var(--muted-fg);
  margin-top: 1rem;
  max-width: 32rem;
}

/* ── Blobs ── */
.blob {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
}

.blob--hero-left {
  top: 25%;
  left: -8rem;
  width: 24rem;
  height: 24rem;
  background: rgba(var(--primary-rgb), 0.05);
  filter: blur(120px);
}

.blob--hero-right {
  bottom: 25%;
  right: -8rem;
  width: 20rem;
  height: 20rem;
  background: rgba(var(--accent-rgb), 0.05);
  filter: blur(100px);
}

.blob--projects {
  top: 33%;
  right: -12rem;
  width: 24rem;
  height: 24rem;
  background: rgba(var(--primary-rgb), 0.03);
  filter: blur(120px);
}

.blob--contact {
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 20rem;
  height: 20rem;
  background: rgba(var(--primary-rgb), 0.05);
  filter: blur(100px);
}

/* ── Reveal / Stagger ── */
.hero-anim {
  opacity: 0;
  transform: translateY(30px);
  animation: fadeInUp 0.6s ease-out var(--hero-delay, 0s) forwards;
}

.hero-anim--right {
  transform: translateX(40px);
  animation: fadeInRight 0.7s ease-out var(--hero-delay, 0s) forwards;
}

.reveal {
  opacity: 0;
  transform: translateY(60px);
  transition:
    opacity   0.7s var(--delay, 0s) ease,
    transform 0.7s var(--delay, 0s) ease;
}

.reveal--visible {
  opacity: 1;
  transform: translate(0, 0);
}

.stagger {
  opacity: 0;
  transform: translateY(40px);
  transition:
    opacity   0.6s calc(var(--i) * 0.15s) ease,
    transform 0.6s calc(var(--i) * 0.15s) ease;
}

.stagger--visible {
  opacity: 1;
  transform: translateY(0);
}

/* ── Gradient text ── */
.gradient {
  background: linear-gradient(
    120deg,
    var(--primary)  0%,
    var(--accent)   40%,
    #fff            50%,
    var(--accent)   60%,
    var(--primary)  100%
  );
  background-size: 220% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 4s linear infinite;
}

/* ══ NAVBAR ══════════════════════════════════════ */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
  transition: all 0.3s;
  animation: fadeInUp 0.6s ease-out;
}

.navbar--scrolled {
  backdrop-filter: blur(12px);
  background: rgba(var(--bg-rgb), 0.85);
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.2);
  border-bottom: 1px solid var(--border);
}

.navbar__inner {
  max-width: 72rem;
  margin: 0 auto;
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.navbar__logo {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--primary);
  background: none;
  border: none;
  cursor: pointer;
}

.navbar__links {
  display: none;
  gap: 2rem;
  list-style: none;
}

.navbar__toggle {
  display: none;
  flex-direction: column;
  gap: 6px;
  padding: 8px;
  background: none;
  border: none;
  cursor: pointer;
}

@media (max-width: 767px) {
  .navbar__toggle { display: flex; }
}

@media (min-width: 768px) {
  .navbar__links { display: flex; }
}

.navbar__link {
  font-size: 0.875rem;
  color: var(--muted-fg);
  background: none;
  border: none;
  cursor: pointer;
  position: relative;
  transition: color 0.2s;
}

.navbar__link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary);
  transition: width 0.3s;
}

.navbar__link:hover        { color: var(--primary); }
.navbar__link:hover::after { width: 100%; }

.bar {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--fg);
  transition: all 0.3s;
}

.bar--top-open { transform: rotate(45deg) translateY(8px); }
.bar--mid-open { opacity: 0; }
.bar--bot-open { transform: rotate(-45deg) translateY(-8px); }

.navbar__mobile {
  backdrop-filter: blur(12px);
  background: rgba(var(--bg-rgb), 0.9);
  border-top: 1px solid var(--border);
}

.navbar__mobile-list {
  display: flex;
  flex-direction: column;
  padding: 1.5rem;
  gap: 1rem;
  list-style: none;
}

.mobile-menu-enter-active,
.mobile-menu-leave-active {
  transition: opacity 0.2s, max-height 0.3s;
  max-height: 300px;
  overflow: hidden;
}

.mobile-menu-enter-from,
.mobile-menu-leave-to {
  opacity: 0;
  max-height: 0;
}

/* ── Dots ── */
.dot {
  display: inline-block;
  border-radius: 50%;
  flex-shrink: 0;
}

.dot--r { width: 10px; height: 10px; background: rgba(239, 68,  68,  0.6); }
.dot--y { width: 10px; height: 10px; background: rgba(var(--primary-rgb), 0.6); }
.dot--g { width: 10px; height: 10px; background: rgba(var(--accent-rgb),  0.6); }

/* ══ HERO ════════════════════════════════════════ */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  overflow: hidden;
}

.hero__inner {
  max-width: 72rem;
  margin: 0 auto;
  padding: 8rem 1.5rem;
  width: 100%;
  display: grid;
  grid-template-columns: 1fr;
  gap: 3rem;
  align-items: center;
}

@media (min-width: 768px) {
  .hero__inner { grid-template-columns: 1fr 1fr; }
}

.badge {
  display: inline-block;
  padding: 0.375rem 1rem;
  border-radius: 9999px;
  background: rgba(var(--primary-rgb), 0.1);
  color: var(--primary);
  font-size: 0.875rem;
  font-weight: 500;
  margin-bottom: 1.5rem;
  border: 1px solid rgba(var(--primary-rgb), 0.2);
}

.hero__name {
  font-size: clamp(2.5rem, 8vw, 4.5rem);
  font-weight: 700;
  margin-bottom: 0.5rem;
}

.bracket {
  color: var(--muted-fg);
  font-size: 0.55em;
  font-weight: 300;
}

.hero__role {
  font-size: clamp(1.25rem, 4vw, 1.875rem);
  font-weight: 500;
  margin-bottom: 1.5rem;
}

.hero__role-hl {
  background: linear-gradient(135deg, var(--primary), var(--accent));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  border-bottom: 2px solid rgba(var(--primary-rgb), 0.5);
  padding-bottom: 4px;
}

.hero__bio {
  color: var(--muted-fg);
  line-height: 1.75;
  max-width: 32rem;
  margin-bottom: 2rem;
}

.hero__cta {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

/* ── Buttons ── */
.btn {
  padding: 0.75rem 1.5rem;
  border-radius: 0.5rem;
  font-weight: 600;
  font-size: 0.875rem;
  cursor: pointer;
  transition: all 0.2s;
  border: none;
}

.btn--primary {
  background: linear-gradient(135deg, var(--primary), var(--accent));
  color: #fff;
  box-shadow: 0 0 20px rgba(var(--primary-rgb), 0.3);
}
.btn--primary:hover { opacity: 0.88; }

.btn--outline {
  background: transparent;
  border: 1px solid rgba(var(--primary-rgb), 0.3);
  color: var(--primary);
}
.btn--outline:hover { background: rgba(var(--primary-rgb), 0.1); }

/* ── Code card ── */
.code-card {
  position: relative;
  padding: 1.5rem;
}

.code-card__pulse-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 340px;
  height: 340px;
  background: radial-gradient(
    circle,
    rgba(var(--primary-rgb), 0.18) 0%,
    transparent 70%
  );
  border-radius: 50%;
  pointer-events: none;
  animation: pulseGlow 4s ease-in-out infinite;
  z-index: 0;
}

.code-card__window {
  position: relative;
  z-index: 1;
  background: rgba(var(--bg-rgb), 0.35);
  border-radius: 1rem;
  overflow: hidden;
  border: 1px solid rgba(var(--primary-rgb), 0.55);
  box-shadow:
    0 25px 60px rgba(0, 0, 0, 0.75),
    0 0 40px rgba(var(--primary-rgb), 0.12),
    inset 0 1px 0 rgba(255, 255, 255, 0.04);
  backdrop-filter: blur(10px);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.code-card__window:hover {
  transform: translateY(-4px);
  box-shadow:
    0 30px 70px rgba(0, 0, 0, 0.65),
    0 0 60px rgba(var(--primary-rgb), 0.2);
}

.code-card__bar {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  border-bottom: 1px solid var(--border);
  background: rgba(0, 0, 0, 0.25);
}

.code-card__file {
  margin-left: 0.75rem;
  font-size: 0.75rem;
  color: var(--muted-fg);
  font-family: monospace;
}

.code-card__body {
  padding: 1.5rem 1.75rem;
  font-family: 'Fira Code', 'Consolas', monospace;
  font-size: 0.9rem;
  line-height: 1.75;
  color: var(--fg);
}

.ind { padding-left: 1.5rem; }

.kw { color: var(--accent); }
.vr { color: var(--fg); }
.mu { color: var(--muted-fg); }
.pr { color: rgba(var(--accent-rgb), 0.85); }
.st { color: var(--primary); }

/* ── Float icons ── */
.float-icon {
  position: absolute;
  z-index: 2;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 0.5rem;
  font-size: 0.7rem;
  font-weight: 700;
  color: #fff;
  letter-spacing: 0.03em;
}

.float-icon--vue {
  top: 0;
  right: 0;
  width: 3rem;
  height: 3rem;
  background: linear-gradient(135deg, var(--primary), var(--accent));
  box-shadow: 0 0 16px rgba(var(--primary-rgb), 0.5);
  animation: float 3s ease-in-out infinite;
}

.float-icon--js {
  bottom: 0.5rem;
  right: 0.25rem;
  width: 2.5rem;
  height: 2.5rem;
  background: rgba(var(--accent-rgb), 0.75);
  box-shadow: 0 0 12px rgba(var(--accent-rgb), 0.4);
  animation: float 3.5s ease-in-out 0.5s infinite;
}

.float-icon--html {
  bottom: 0.5rem;
  left: 0.25rem;
  width: 2.75rem;
  height: 2.75rem;
  background: rgba(var(--primary-rgb), 0.6);
  box-shadow: 0 0 12px rgba(var(--primary-rgb), 0.35);
  animation: float 3.2s ease-in-out 0.3s infinite;
}

.float-icon--css {
  top: 0;
  left: 0;
  width: 2.5rem;
  height: 2.5rem;
  background: linear-gradient(
    135deg,
    rgba(var(--accent-rgb),  0.7),
    rgba(var(--primary-rgb), 0.7)
  );
  box-shadow: 0 0 12px rgba(var(--accent-rgb), 0.35);
  animation: float 2.8s ease-in-out 0.7s infinite;
}

/* ══ TECH CARDS ══════════════════════════════════ */
.tech-grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: 1fr;
}

@media (min-width: 640px)  { .tech-grid { grid-template-columns: 1fr 1fr; } }
@media (min-width: 1024px) { .tech-grid { grid-template-columns: repeat(4, 1fr); } }

.tech-card {
  padding: 1.5rem;
  border-radius: 0.75rem;
  background: var(--card);
  border: 1px solid var(--border);
  transition: border-color 0.3s, box-shadow 0.3s;
  height: 100%;
}

.tech-card:hover {
  border-color: rgba(var(--primary-rgb), 0.3);
  box-shadow: 0 0 20px rgba(var(--primary-rgb), 0.1);
}

.tech-card__icon {
  font-size: 2rem;
  margin-bottom: 1rem;
}

.tech-card__name {
  font-size: 1.125rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
  transition: color 0.2s;
}
.tech-card:hover .tech-card__name { color: var(--primary); }

.tech-card__desc {
  font-size: 0.875rem;
  color: var(--muted-fg);
  line-height: 1.6;
}

/* ══ PROJECT CARDS ═══════════════════════════════ */
.proj-grid {
  display: grid;
  gap: 1.25rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .proj-grid {
    gap: 1.5rem;
    grid-template-columns: 1fr 1fr;
  }
}

.proj-grid > .stagger {
  display: flex;
  width: 100%;
}

/* Último card sozinho ocupa a linha toda */
@media (min-width: 768px) {
  .proj-grid > .stagger:last-child:nth-child(odd) {
    grid-column: 1 / -1;
  }
}

.proj-card {
  display: flex;
  flex-direction: column;
  padding: 1.5rem;
  border-radius: 0.75rem;
  background: var(--card);
  border: 1px solid var(--border);
  text-decoration: none;
  width: 100%;
  height: 100%;
  transition: border-color 0.3s, box-shadow 0.3s;
}

.proj-card:hover {
  border-color: rgba(var(--primary-rgb), 0.3);
  box-shadow: 0 0 20px rgba(var(--primary-rgb), 0.1);
}

.proj-card__bar {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
  padding-bottom: 1rem;
  border-bottom: 1px solid var(--border);
}

.proj-card__url {
  flex: 1;
  margin-left: 0.75rem;
  height: 1.5rem;
  border-radius: 0.25rem;
  background: rgba(var(--muted-rgb), 0.5);
  display: flex;
  align-items: center;
  padding: 0 0.75rem;
  font-size: 0.625rem;
  color: var(--muted-fg);
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.proj-card__title {
  font-size: 1.25rem;
  font-weight: 600;
  color: var(--fg);
  margin-bottom: 0.5rem;
  display: flex;
  align-items: center;
  gap: 0.5rem;
  transition: color 0.2s;
}
.proj-card:hover .proj-card__title { color: var(--primary); }

.proj-card__ext {
  opacity: 0;
  color: var(--primary);
  transition: opacity 0.2s;
  flex-shrink: 0;
}
.proj-card:hover .proj-card__ext { opacity: 1; }

.proj-card__desc {
  font-size: 0.875rem;
  color: var(--muted-fg);
  line-height: 1.6;
  margin-bottom: 1rem;
  flex: 1;
}

.proj-card__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  padding: 0.25rem 0.75rem;
  border-radius: 9999px;
  font-size: 0.75rem;
  font-weight: 500;
  background: rgba(var(--primary-rgb), 0.1);
  color: var(--primary);
  border: 1px solid rgba(var(--primary-rgb), 0.2);
}

/* ══ CONTACT ═════════════════════════════════════ */
.contact-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
  margin: 2rem 0 3rem;
}

.contact-btn {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 1.5rem;
  border-radius: 0.75rem;
  background: var(--card);
  border: 1px solid var(--border);
  text-decoration: none;
  color: var(--muted-fg);
  font-size: 0.875rem;
  transition: border-color 0.3s, box-shadow 0.3s, color 0.2s;
}

.contact-btn svg { color: var(--primary); flex-shrink: 0; }

.contact-btn:hover {
  border-color: rgba(var(--primary-rgb), 0.3);
  box-shadow: 0 0 20px rgba(var(--primary-rgb), 0.1);
  color: var(--fg);
}

/* ══ FOOTER ══════════════════════════════════════ */
.footer {
  border-top: 1px solid var(--border);
  padding-top: 2rem;
}

.footer__text {
  color: var(--muted-fg);
  font-size: 0.875rem;
}
</style>
