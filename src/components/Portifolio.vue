<template>
  <div class="min-h-screen">
    <div class="grain-overlay" />

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
          <div class="hero-anim">
            <div class="status-badge">
              <span class="status-dot" />
              Disponível para novos projetos
            </div>
          </div>
          <div class="hero-anim">
            <h1 class="hero__name">
              <span class="bracket">&lt;</span>
              <span class="gradient">Jonatas</span>
              <span class="bracket">/&gt;</span>
            </h1>
          </div>
          <div class="hero-anim">
            <h2 class="hero__role">
              Desenvolvedor <span class="hero__role-hl">Frontend Fullstack</span>
            </h2>
          </div>
          <div class="hero-anim">
            <p class="hero__bio">
              Especialista em construir interfaces modernas, intuitivas e de alta performance.
              Transformando códigos complexos em experiências digitais memoráveis com Vue.js e ecossistema moderno.
            </p>
          </div>
          <div class="hero-anim">
            <div class="hero__cta">
              <button class="btn btn--primary" @click="scrollTo('#projects')">
                Ver Projetos
                <svg
                  fill="none"
                  height="18"
                  stroke="currentColor"
                  stroke-linecap="round"
                  stroke-linejoin="round"
                  stroke-width="2"
                  viewBox="0 0 24 24"
                  width="18"
                  xmlns="http://www.w3.org/2000/svg"
                >
                  <path d="m12 5 7 7-7 7" />
                  <path d="M5 12h14" />
                </svg>
              </button>
              <button class="btn btn--outline" @click="scrollTo('#contact')">Contato</button>
            </div>
          </div>
        </div>

        <div class="hero__visual">
          <div class="code-card">
            <div class="code-card__pulse-glow" />
            <div class="code-card__window">
              <div class="code-card__bar">
                <div class="code-card__dots">
                  <span class="dot dot--r" /><span class="dot dot--y" /><span class="dot dot--g" />
                </div>
                <span class="code-card__file">Developer.vue</span>
              </div>
              <div class="code-card__body">
                <div class="code-line"><span class="kw">const</span> <span class="vr">skills</span> <span class="mu">=</span> <span class="mu">[</span></div>
                <div class="code-line ind"><span class="st">'Vue.js'</span><span class="mu">,</span> <span class="st">'TypeScript'</span><span class="mu">,</span></div>
                <div class="code-line ind"><span class="st">'Node.js'</span><span class="mu">,</span> <span class="st">'Vuetify'</span></div>
                <div class="code-line"><span class="mu">];</span></div>
                <div class="code-line"><span class="kw">if</span> <span class="mu">(</span><span class="vr">isAwesomeProject</span><span class="mu">)</span> <span class="mu">{</span></div>
                <div class="code-line ind"><span class="vr">hire</span><span class="mu">(</span><span class="st">'Jonatas'</span><span class="mu">);</span></div>
                <div class="code-line"><span class="mu">}</span></div>
              </div>
            </div>

            <!-- Float Icons -->
            <div class="float-asset float-asset--1">
              <i class="devicon-vuejs-plain colored" />
            </div>
            <div class="float-asset float-asset--2">
              <i class="devicon-typescript-plain colored" />
            </div>
            <div class="float-asset float-asset--3">
              <i class="devicon-javascript-plain colored" />
            </div>
            <div class="float-asset float-asset--4">
              <i class="devicon-vitejs-plain colored" />
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- ===== TECNOLOGIAS ===== -->
    <section id="tech" class="section">
      <div class="section__divider" />
      <div class="container">
        <div class="section__head">
          <h2 class="section__title">Principais <span class="gradient">Tecnologias</span></h2>
          <p class="section__sub">Ferramentas e tecnologias que utilizo para construir interfaces incríveis</p>
        </div>

        <div class="tech-grid">
          <div
            v-for="tech in techs"
            :key="tech.name"
            class="tech-card-wrapper"
          >
            <div class="tech-card">
              <div class="tech-card__icon">
                <i :class="[tech.icon, 'tech-icon']" />
              </div>
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
        <div class="section__head">
          <h2 class="section__title">Meus <span class="gradient">Projetos</span></h2>
          <p class="section__sub">Projetos focados na construção de interfaces modernas e funcionais</p>
        </div>

        <div class="proj-grid">
          <div
            v-for="proj in projects"
            :key="proj.title"
            class="proj-card-wrapper"
          >
            <a class="proj-card" :href="proj.link" rel="noopener noreferrer" target="_blank">
              <div class="proj-card__bar">
                <span class="dot dot--r" /><span class="dot dot--y" /><span class="dot dot--g" />
                <div class="proj-card__url">localhost:3000/{{ proj.title.toLowerCase().replace(/\s/g,'-') }}</div>
              </div>
              <div class="proj-card__content">
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
                  ><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6" /><polyline points="15 3 21 3 21 9" /><line x1="10" x2="21" y1="14" y2="3" /></svg>
                </h3>
                <p class="proj-card__desc">{{ proj.description }}</p>
                <div class="proj-card__tags">
                <span v-for="tag in proj.tags" :key="tag" class="tag">{{ tag }}</span>
                </div>
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
        <div style="text-align:center">
          <h2 class="section__title">Vamos <span class="gradient">Conversar</span>?</h2>
          <p class="section__sub" style="margin-inline:auto">Estou disponível para novos projetos e oportunidades. Entre em contato!</p>
        </div>

        <div>
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
              ><rect
                height="16"
                rx="2"
                width="20"
                x="2"
                y="4"
              /><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7" /></svg>
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
              ><path d="M15 22v-4a4.8 4.8 0 0 0-1-3.2c3 0 6-2 6-5.5.08-1.25-.27-2.48-1-3.5.28-1.15.28-2.35 0-3.5 0 0-1 0-3 1.5-2.64-.5-5.36-.5-8 0C6 2 5 2 5 2c-.3 1.15-.3 2.35 0 3.5A5.4 5.4 0 0 0 4 9c0 3.5 3 5.5 6 5.5-.39.49-.68 1.05-.85 1.65S8.93 17.38 9 18v4" /><path d="M9 18c-4.51 2-5-2-7-2" /></svg>
              <span>GitHub</span>
            </a>
            <a class="contact-btn" href="https://www.linkedin.com/in/jonatasgomess/" rel="noopener noreferrer" target="_blank">
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
              ><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z" /><rect height="12" width="4" x="2" y="9" /><circle cx="4" cy="4" r="2" /></svg>
              <span>LinkedIn</span>
            </a>
          </div>
        </div>

        <div>
          <div class="footer">
            <p class="footer__text">
              &lt;<span style="color:var(--primary)">Jonatas da Silva Gomes</span> /&gt;  {{ year }}
            </p>
          </div>
        </div>
      </div>
    </section>

  </div>
</template>

<script setup>
  import { gsap } from 'gsap'
  import { ScrollTrigger } from 'gsap/ScrollTrigger'
  import { onMounted, onUnmounted, ref } from 'vue'

  gsap.registerPlugin(ScrollTrigger)

  const year = new Date().getFullYear()

  const navLinks = [
    { label: 'Início', href: '#hero' },
    { label: 'Tecnologias', href: '#tech' },
    { label: 'Projetos', href: '#projects' },
    { label: 'Contato', href: '#contact' },
  ]

  const techs = [
    {
      name: 'Vue.js',
      description: 'Framework que escolhi para desenvolver interfaces modernas e reativas.',
      icon: 'devicon-vuejs-plain colored',
    },
    {
      name: 'TypeScript',
      description: 'Superset do JavaScript que adiciona tipagem estática e segurança ao código.',
      icon: 'devicon-typescript-plain colored',
    },
    {
      name: 'Vuetify',
      description: 'Biblioteca de componentes UI para Vue que segue as diretrizes do Material Design.',
      icon: 'devicon-vuetify-plain colored',
    },
    {
      name: 'JavaScript',
      description: 'Linguagem responsável pela lógica e interatividade das aplicações web.',
      icon: 'devicon-javascript-plain colored',
    },
    {
      name: 'Vite',
      description: 'Ferramenta de build extremamente rápida que otimiza o fluxo de desenvolvimento.',
      icon: 'devicon-vitejs-plain colored',
    },
    {
      name: 'HTML',
      description: 'Linguagem responsável por estruturar todo o conteúdo das páginas web.',
      icon: 'devicon-html5-plain colored',
    },
    {
      name: 'CSS',
      description: 'Estiliza e organiza o layout das páginas, criando interfaces visuais atraentes.',
      icon: 'devicon-css3-plain colored',
    },
    {
      name: 'Git',
      description: 'Sistema de controle de versão essencial para o gerenciamento de colaborativo.',
      icon: 'devicon-git-plain colored',
    },
  ]

  const projects = [
    { title: 'Tela de Login', description: 'Interface de login moderna com validação e design responsivo.', tags: ['Vue', 'Vuetify', 'JavaScript'], link: 'https://tela-login-beryl.vercel.app/' },
    { title: 'Filmes e Séries', description: 'Catálogo de filmes e séries consumindo API externa com busca e filtros.', tags: ['Vue', 'Vuetify', 'API', 'JavaScript'], link: 'https://filmes-series-psi.vercel.app/' },
    { title: 'Viagem de Chihiro', description: 'Landing page temática com animações e design imersivo.', tags: ['HTML', 'CSS'], link: 'https://viagem-de-chihiro-theta.vercel.app/' },
    { title: 'Jordan Shoes', description: 'Site portfolio com design moderno e código limpo.', tags: ['Vue', 'CSS', 'JavaScript'], link: 'https://jordanshoes-gilt.vercel.app/' },
    { title: 'Dev Blog', description: 'Plataforma de blog moderna para compartilhamento de artigos técnicos.', tags: ['Vue', 'Vite', 'JavaScript'], link: 'https://blog-three-gilt-75.vercel.app/' },
    { title: 'Premium Coffee', description: 'Landing page elegante para uma cafeteria gourmet com visual sofisticado.', tags: ['Vue', 'Vuetify', 'CSS'], link: 'https://coffe-iota-eight.vercel.app/' },
  ]

  const scrolled = ref(false)
  const mobileOpen = ref(false)

  function scrollTo (href) {
    mobileOpen.value = false
    document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
  }

  function onScroll () {
    scrolled.value = window.scrollY > 40
  }
  onMounted(() => window.addEventListener('scroll', onScroll))
  onUnmounted(() => window.removeEventListener('scroll', onScroll))

  const techHead = ref(null)

  onMounted(() => {
    // GSAP Hero Animations
    const tl = gsap.timeline({ defaults: { ease: 'power4.out', duration: 1.2 } })

    tl.to('.hero-anim', {
      y: 0,
      opacity: 1,
      stagger: 0.15,
      delay: 0.3,
    })

    tl.from('.hero__visual', {
      x: 60,
      opacity: 0,
      duration: 1.4,
    }, '-=1')

    // Floating assets animation
    gsap.to('.float-asset', {
      y: -20,
      duration: 'random(2, 4)',
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
      stagger: {
        each: 0.4,
        from: 'random',
      },
    })

    // Floating animation for code card
    gsap.to('.code-card', {
      y: -15,
      rotation: 2,
      duration: 4,
      repeat: -1,
      yoyo: true,
      ease: 'sine.inOut',
    })

    // Scroll Animations
    gsap.from('.tech-card', {
      scrollTrigger: {
        trigger: '#tech',
        start: 'top 85%',
        toggleActions: 'play none none none',
      },
      y: 60,
      opacity: 0,
      stagger: 0.15,
      duration: 1,
      ease: 'power3.out',
      clearProps: 'all',
    })

    gsap.from('.proj-card', {
      scrollTrigger: {
        trigger: '#projects',
        start: 'top 85%',
        toggleActions: 'play none none none',
      },
      y: 60,
      opacity: 0,
      stagger: 0.2,
      duration: 1.2,
      ease: 'power3.out',
      clearProps: 'all',
    })
  })
</script>

<style>
#app {
  --primary:     #7c4dff;
  --primary-rgb: 124, 77, 255;
  --accent:      #b388ff;
  --accent-rgb:  179, 136, 255;
  --bg:          #030712;
  --bg-rgb:      3, 7, 18;
  --fg:          #f9fafb;
  --muted-fg:    #9ca3af;
  --card:        rgba(17, 24, 39, 0.7);
  --border:      rgba(255, 255, 255, 0.06);
  --glass:       rgba(255, 255, 255, 0.03);
  --glass-border: rgba(255, 255, 255, 0.08);
  --shadow:      0 8px 32px 0 rgba(0, 0, 0, 0.37);
  --font-main:   'Inter', 'Outfit', sans-serif;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background: var(--bg);
  background-image:
    radial-gradient(at 0% 0%, rgba(var(--primary-rgb), 0.1) 0px, transparent 50%),
    radial-gradient(at 100% 0%, rgba(var(--accent-rgb), 0.1) 0px, transparent 50%);
  color: var(--fg);
  font-family: var(--font-main);
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

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
  50% { transform: translateY(-8px); }
}

.grain-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  z-index: 9999;
  opacity: 0.02;
  /* Use a data-uri or simple CSS noise if the external URL is blocked */
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3F%3E%3Cfilter id='noiseFilter'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.65' numOctaves='3' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23noiseFilter)'/%3E%3C/svg%3E");
  filter: contrast(150%) brightness(150%);
}
</style>

<style scoped>
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
  background: var(--bg);
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
  flex-direction:column ;
  align-items: center;
  justify-content: center;
  margin-bottom: 4rem;
}

.section__tag {
  color: var(--primary);
  font-size: .875rem;
  font-weight: 500;
}

.section__title {
  font-size: clamp(2rem, 5vw, 3rem);
  font-weight: 800;
  letter-spacing: -0.02em;
  color: var(--fg);
}

.section__sub {
  color: var(--muted-fg);
  margin-top: 1.25rem;
  font-size: 1.125rem;
  max-width: 36rem;
  line-height: 1.6;
}

/* ── Blobs ── */
.blob {
  position: absolute;
  border-radius: 50%;
  pointer-events: none;
  filter: blur(120px);
  z-index: 1;
}

.blob--hero-left {
  top: 10%;
  left: -10%;
  width: 40vw;
  height: 40vw;
  background: rgba(var(--primary-rgb), 0.15);
}

.blob--hero-right {
  bottom: 20%;
  right: -5%;
  width: 35vw;
  height: 35vw;
  background: rgba(var(--accent-rgb), 0.1);
}

.blob--projects {
  top: 33%;
  right: -12rem;
  width: 24rem;
  height: 24rem;
  background: rgba(var(--primary-rgb), .03);
  filter: blur(120px);
}

.blob--contact {
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 20rem;
  height: 20rem;
  background: rgba(var(--primary-rgb), .05);
  filter: blur(100px);
}

/* ── Hero GSAP ── */
/* ── Hero GSAP ── */
.hero-anim {
  opacity: 0;
  transform: translateY(40px);
  will-change: transform, opacity;
}

/* ── Reveal ── */
.reveal {
  opacity: 0;
  transform: translateY(60px);
  transition: opacity .7s var(--delay, 0s) ease, transform .7s var(--delay, 0s) ease;
}

.reveal--visible {
  opacity: 1;
  transform: translate(0, 0);
}

.stagger {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity .6s calc(var(--i) * .15s) ease, transform .6s calc(var(--i) * .15s) ease;
}

.stagger--visible {
  opacity: 1;
  transform: translateY(0);
}

.gradient {
  background: linear-gradient(
    120deg,
    var(--primary)   0%,
    var(--accent)    40%,
    #fff             50%,
    var(--accent)    60%,
    var(--primary)   100%
  );
  background-size: 220% auto;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: shimmer 4s linear infinite;
}

@keyframes shimmer {
  0%   { background-position: 0% center; }
  100% { background-position: 220% center; }
}
/* ── Navbar ── */
.navbar {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 50;
  transition: all .4s cubic-bezier(0.4, 0, 0.2, 1);
  padding: 1rem 0;
}

.navbar--scrolled {
  backdrop-filter: blur(16px);
  background: rgba(var(--bg-rgb), 0.7);
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.1);
  border-bottom: 1px solid var(--glass-border);
  padding: 0.75rem 0;
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

/*
  Toggle: escondido por padrão no desktop.
  Todas as propriedades ficam aqui num bloco único
  para evitar que uma segunda declaração sobrescreva o display.
*/
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
  .navbar__toggle {
    display: flex;
  }
}

@media (min-width: 768px) {
  .navbar__links {
    display: flex;
  }
}

.navbar__link {
  font-size: .875rem;
  color: var(--muted-fg);
  background: none;
  border: none;
  cursor: pointer;
  position: relative;
  transition: color .2s;
}

.navbar__link::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--primary);
  transition: width .3s;
}

.navbar__link:hover {
  color: var(--primary);
}

.navbar__link:hover::after {
  width: 100%;
}

.bar {
  display: block;
  width: 24px;
  height: 2px;
  background: var(--fg);
  transition: all .3s;
}

.bar--top-open {
  transform: rotate(45deg) translateY(8px);
}

.bar--mid-open {
  opacity: 0;
}

.bar--bot-open {
  transform: rotate(-45deg) translateY(-8px);
}

.navbar__mobile {
  backdrop-filter: blur(12px);
  background: rgba(var(--bg-rgb), .9);
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
  transition: opacity .2s, max-height .3s;
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

.dot--r {
  width: 10px;
  height: 10px;
  background: rgba(239, 68, 68, .6);
}

.dot--y {
  width: 10px;
  height: 10px;
  background: rgba(var(--primary-rgb), .6);
}

.dot--g {
  width: 10px;
  height: 10px;
  background: rgba(var(--accent-rgb), .6);
}

/* ── Hero ── */
.hero {
  position: relative;
  min-height: 100vh;
  display: flex;
  align-items: center;
  padding: 6rem 0;
  overflow: hidden;
  background: var(--bg);
}

.hero__inner {
  position: relative;
  width: 100%;
  max-width: 72rem;
  margin: 0 auto;
  padding: 0 1.5rem;
  display: flex;
  flex-direction: column;
  gap: 3rem;
  z-index: 2;
  text-align: center;
}

@media (min-width: 1024px) {
  .hero__inner {
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    text-align: left;
    gap: 4rem;
  }
}

.hero__content {
  flex: 1;
  max-width: 38rem;
  margin: 0 auto;
}

@media (min-width: 1024px) {
  .hero__content {
    margin: 0;
  }
}

.status-badge {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.5rem 1rem;
  background: rgba(var(--primary-rgb), 0.1);
  border: 1px solid rgba(var(--primary-rgb), 0.2);
  border-radius: 2rem;
  font-size: 0.8125rem;
  font-weight: 600;
  color: var(--primary);
  margin-bottom: 2rem;
}

.status-dot {
  width: 8px;
  height: 8px;
  background: var(--primary);
  border-radius: 50%;
  box-shadow: 0 0 12px var(--primary);
  animation: pulseStatus 2s infinite;
}

@keyframes pulseStatus {
  0% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(var(--primary-rgb), 0.7); }
  70% { transform: scale(1); box-shadow: 0 0 0 10px rgba(var(--primary-rgb), 0); }
  100% { transform: scale(0.95); box-shadow: 0 0 0 0 rgba(var(--primary-rgb), 0); }
}

.hero__name {
  font-size: clamp(2.5rem, 10vw, 5rem);
  font-weight: 900;
  line-height: 1.1;
  letter-spacing: -0.04em;
  margin-bottom: 1.5rem;
}

.hero__role {
  font-size: clamp(1.25rem, 5vw, 2.25rem);
  font-weight: 800;
  color: var(--fg);
  margin-bottom: 2rem;
}

.hero__role-hl {
  color: var(--primary);
  position: relative;
}

.hero__bio {
  font-size: 1.125rem;
  color: var(--muted-fg);
  line-height: 1.7;
  margin-bottom: 3rem;
  max-width: 32rem;
}

.hero__cta {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
  justify-content: center;
}

@media (min-width: 1024px) {
  .hero__cta {
    gap: 1.25rem;
    justify-content: flex-start;
  }
}

.btn {
  display: inline-flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.875rem 2rem;
  border-radius: 0.75rem;
  font-weight: 700;
  font-size: 0.9375rem;
  cursor: pointer;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  border: none;
}

.btn--primary {
  background: linear-gradient(135deg, var(--primary), var(--accent));
  color: #fff;
  box-shadow: 0 0 20px rgba(var(--primary-rgb), .3);
}

.btn--primary:hover {
  opacity: .88;
}

.btn--outline {
  background: transparent;
  border: 1px solid rgba(var(--primary-rgb), .3);
  color: var(--primary);
}

.btn--outline:hover {
  background: rgba(var(--primary-rgb), .1);
}

/* ── Code card ── */
.code-card {
  position: relative;
  width: 100%;
  max-width: 480px;
  margin: 0 auto;
}

.code-card__pulse-glow {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 400px;
  height: 400px;
  background: radial-gradient(
    circle,
    rgba(var(--primary-rgb), 0.15) 0%,
    transparent 70%
  );
  border-radius: 50%;
  filter: blur(40px);
  pointer-events: none;
  animation: pulseGlow 4s ease-in-out infinite;
  z-index: 0;
}

.code-card__window {
  position: relative;
  z-index: 1;
  background: rgba(17, 24, 39, 0.8);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: var(--shadow);
}

.code-card__bar {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1rem;
  background: rgba(255, 255, 255, 0.05);
  border-bottom: 1px solid var(--glass-border);
}

.code-card__file {
  margin-left: 1rem;
  font-size: 0.75rem;
  font-family: monospace;
  color: var(--muted-fg);
  opacity: 0.8;
}

.code-card__body {
  padding: 1.5rem;
  font-family: 'Fira Code', 'Monaco', 'Consolas', monospace;
  font-size: 0.875rem;
  line-height: 1.6;
}

.kw { color: #c678dd; } /* const */
.vr { color: #e06c75; } /* name */
.mu { color: #abb2bf; } /* punct */
.pr { color: #d19a66; } /* prop */
.st { color: #98c379; } /* string */

.ind { padding-left: 1.5rem; }

.float-asset {
  position: absolute;
  z-index: 2;
  width: 3rem;
  height: 3rem;
  background: rgba(var(--bg-rgb), 0.8);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 1rem;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.4);
}

@media (min-width: 768px) {
  .float-asset {
    width: 4rem;
    height: 4rem;
    font-size: 2rem;
    border-radius: 1.25rem;
  }
}

.float-asset--1 { top: -1.5rem; left: 15%; }
.float-asset--2 { top: 20%; right: -1rem; }
.float-asset--3 { bottom: 15%; left: -1.5rem; }
.float-asset--4 { bottom: -2rem; right: 20%; }

@media (min-width: 768px) {
  .float-asset--1 { top: -2rem; left: 10%; }
  .float-asset--2 { top: 25%; right: -2rem; }
  .float-asset--3 { bottom: 20%; left: -3rem; }
  .float-asset--4 { bottom: -2.5rem; right: 15%; }
}

/* ── Tech cards ── */
.tech-grid {
  display: grid;
  gap: 1.5rem;
  grid-template-columns: 1fr;
}

@media (min-width: 640px) {
  .tech-grid {
    grid-template-columns: 1fr 1fr;
  }
}

@media (min-width: 1024px) {
  .tech-grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

.tech-card {
  padding: 2rem;
  background: var(--glass);
  backdrop-filter: blur(8px);
  border: 1px solid var(--glass-border);
  border-radius: 1.25rem;
  text-align: center;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  height: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.tech-card:hover {
  transform: translateY(-8px);
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(var(--primary-rgb), 0.3);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.2);
}

.tech-card__icon {
  width: 3.5rem;
  height: 3.5rem;
  margin-bottom: 2rem;
  display: flex;
  align-items: center;
  justify-content: center;
}

.tech-icon {
  font-size: 3.5rem;
  filter: drop-shadow(0 0 10px rgba(var(--primary-rgb), 0.2));
}

.tech-card__icon svg {
  width: 100%;
  height: 100%;
  object-fit: contain;
}

.tech-card__name {
  font-size: 1.125rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--fg);
}

.tech-card__desc {
  font-size: 0.875rem;
  color: var(--muted-fg);
  line-height: 1.6;
}

/* ── Project cards ── */
.proj-grid {
  display: grid;
  gap: 2rem;
  grid-template-columns: 1fr;
}

@media (min-width: 768px) {
  .proj-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

.proj-card {
  display: flex;
  flex-direction: column;
  background: var(--glass);
  backdrop-filter: blur(12px);
  border: 1px solid var(--glass-border);
  border-radius: 1.5rem;
  text-decoration: none;
  height: 100%;
  transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
  overflow: hidden;
  box-shadow: var(--shadow);
}

.proj-card:hover {
  transform: translateY(-12px) scale(1.02);
  background: rgba(255, 255, 255, 0.06);
  border-color: rgba(var(--primary-rgb), 0.4);
  box-shadow: 0 40px 80px rgba(0, 0, 0, 0.4);
}

.proj-card__bar {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem 1.5rem;
  background: rgba(255, 255, 255, 0.03);
  border-bottom: 1px solid var(--glass-border);
}

.proj-card__url {
  flex: 1;
  margin-left: 0.5rem;
  font-family: monospace;
  font-size: 0.7rem;
  color: var(--muted-fg);
  background: rgba(0, 0, 0, 0.2);
  padding: 0.25rem 0.75rem;
  border-radius: 0.5rem;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.proj-card__content {
  padding: 2rem;
  display: flex;
  flex-direction: column;
  flex: 1;
}

.proj-card__title {
  font-size: 1.5rem;
  font-weight: 800;
  color: var(--fg);
  margin-bottom: 1rem;
  display: flex;
  align-items: center;
  gap: 0.75rem;
}

.proj-card__ext {
  color: var(--primary);
  opacity: 0.4;
  transition: all 0.3s;
}

.proj-card:hover .proj-card__ext {
  opacity: 1;
  transform: translate(2px, -2px);
}

.proj-card__desc {
  font-size: 0.9375rem;
  color: var(--muted-fg);
  line-height: 1.7;
  margin-bottom: 2rem;
  flex: 1;
}

.proj-card__tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
}

.tag {
  padding: 0.375rem 1rem;
  background: rgba(var(--primary-rgb), 0.1);
  color: var(--primary);
  border: 1px solid rgba(var(--primary-rgb), 0.2);
  border-radius: 2rem;
  font-size: 0.75rem;
  font-weight: 600;
  transition: all 0.3s;
}

.proj-card:hover .tag {
  background: rgba(var(--primary-rgb), 0.2);
  border-color: var(--primary);
}

/* ── Contact ── */
.contact-links {
  display: flex;
  justify-content: center;
  gap: 1.5rem;
  flex-wrap: wrap;
  margin: 3rem 0;
}

.contact-btn {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 1rem 2rem;
  border-radius: 1rem;
  background: var(--glass);
  backdrop-filter: blur(8px);
  border: 1px solid var(--glass-border);
  text-decoration: none;
  color: var(--fg);
  font-size: 0.9375rem;
  font-weight: 600;
  transition: all 0.3s cubic-bezier(0.4, 0, 0.2, 1);
  box-shadow: var(--shadow);
}

.contact-btn svg {
  color: var(--primary);
  flex-shrink: 0;
  transition: transform 0.3s;
}

.contact-btn:hover {
  transform: translateY(-4px);
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(var(--primary-rgb), 0.3);
}

.contact-btn:hover svg {
  transform: scale(1.1);
}

.footer {
  border-top: 1px solid var(--border);
  padding-top: 2rem;
}

.footer__text {
  color: var(--muted-fg);
  font-size: .875rem;
}
</style>
