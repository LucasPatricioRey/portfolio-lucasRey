<script setup>
import { projects } from "../data/projects";

const showcaseProjects = projects.filter((project) => project.featured).slice(0, 3);
const primaryProject = showcaseProjects[0];
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-copy">
      <p class="eyebrow">Disponible para oportunidades trainee y junior</p>

      <h1>
        Frontend junior que ya construye <span>productos full-stack deployados</span>.
      </h1>

      <p class="intro">
        Soy Lucas Rey. Hice apps con turnos, e-commerce, dashboards, autenticacion,
        APIs y MongoDB. Busco una oportunidad junior para aportar en producto desde
        el primer dia.
      </p>

      <div class="hero-actions" aria-label="Acciones principales">
        <a href="#featured-project" class="btn btn-primary">Ver caso REDO</a>
        <a href="#projects" class="btn btn-secondary">Ver proyectos</a>
        <a href="/cv-lucas-rey.pdf" class="btn btn-ghost" download>Descargar CV</a>
      </div>

      <ul class="hero-metrics" aria-label="Pruebas rapidas">
        <li>
          <strong>6</strong>
          <span>proyectos publicados</span>
        </li>
        <li>
          <strong>4</strong>
          <span>apps full-stack</span>
        </li>
        <li>
          <strong>Auth</strong>
          <span>roles, APIs y MongoDB</span>
        </li>
      </ul>
    </div>

    <div class="hero-visual">
      <div class="showcase-panel glass-panel">
        <div class="showcase-header">
          <div>
            <span>Showroom</span>
            <strong>Apps publicadas</strong>
          </div>
          <a :href="primaryProject.demo" target="_blank" rel="noopener noreferrer">Demo principal</a>
        </div>

        <a
          class="main-preview"
          :href="primaryProject.demo"
          target="_blank"
          rel="noopener noreferrer"
          :aria-label="`Abrir demo de ${primaryProject.title}`"
        >
          <img
            :src="primaryProject.preview"
            :alt="`Vista previa de ${primaryProject.title}`"
            fetchpriority="high"
          >
          <div class="preview-overlay">
            <span>{{ primaryProject.eyebrow }}</span>
            <h2>{{ primaryProject.title }}</h2>
            <p>{{ primaryProject.category }}</p>
          </div>
        </a>

        <div class="mini-projects" aria-label="Proyectos destacados">
          <a
            v-for="project in showcaseProjects"
            :key="project.title"
            class="mini-project"
            :href="project.demo"
            target="_blank"
            rel="noopener noreferrer"
          >
            <img :src="project.preview" :alt="`Miniatura de ${project.title}`" loading="lazy">
            <span>{{ project.title }}</span>
            <small>{{ project.category }}</small>
          </a>
        </div>
      </div>

      <div class="profile-strip glass-panel">
        <picture>
          <source srcset="/lucas-rey-avatar.webp" type="image/webp">
          <img src="/lucas-rey-avatar.png" alt="Avatar ilustrado de Lucas Rey" loading="lazy">
        </picture>
        <div>
          <strong>Lucas Rey</strong>
          <p>Vue, Node.js, Express, MongoDB, JWT, Vercel y Render.</p>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: calc(100vh - 112px);
  display: grid;
  grid-template-columns: minmax(0, 0.96fr) minmax(360px, 1.04fr);
  align-items: center;
  gap: 42px;
  padding-top: 42px;
  position: relative;
}

.hero-copy,
.hero-visual {
  position: relative;
  z-index: 1;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  max-width: 100%;
  margin-bottom: 18px;
  padding: 10px 14px;
  border: 1px solid rgba(54, 211, 153, 0.2);
  border-radius: 999px;
  background: rgba(54, 211, 153, 0.09);
  color: #7ff0c1;
  font-weight: 800;
}

.eyebrow::before {
  content: "";
  width: 9px;
  height: 9px;
  flex: 0 0 9px;
  border-radius: 50%;
  background: #35f08a;
  box-shadow: 0 0 18px rgba(53, 240, 138, 0.76);
}

h1 {
  max-width: 13.4ch;
  margin-bottom: 20px;
  font-size: clamp(2.85rem, 4.9vw, 4.85rem);
  line-height: 0.99;
}

h1 span {
  color: var(--accent-soft);
}

.intro {
  max-width: 630px;
  color: var(--muted);
  line-height: 1.82;
  font-size: 1.06rem;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin: 24px 0 24px;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 48px;
  padding: 13px 18px;
  border-radius: 12px;
  font-weight: 850;
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease, box-shadow 0.25s ease;
}

.btn:hover {
  transform: translateY(-3px);
}

.btn-primary {
  background: linear-gradient(135deg, var(--accent), #ffb15f);
  color: #081120;
  box-shadow: 0 18px 42px rgba(255, 122, 24, 0.22);
}

.btn-secondary {
  background: rgba(93, 214, 255, 0.12);
  border: 1px solid rgba(93, 214, 255, 0.24);
  color: #dff8ff;
}

.btn-ghost {
  border: 1px solid rgba(168, 180, 200, 0.25);
  color: var(--text);
}

.hero-metrics {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 12px;
}

.hero-metrics li {
  min-height: 92px;
  padding: 16px;
  border: 1px solid rgba(168, 180, 200, 0.18);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.045);
}

.hero-metrics strong {
  display: block;
  margin-bottom: 7px;
  color: var(--accent-soft);
  font-size: 1.55rem;
  line-height: 1;
}

.hero-metrics span {
  color: var(--muted);
  font-size: 0.92rem;
  line-height: 1.35;
}

.hero-visual {
  display: grid;
  gap: 16px;
}

.showcase-panel,
.profile-strip {
  border-radius: 24px;
}

.showcase-panel {
  padding: 18px;
  overflow: hidden;
  background:
    linear-gradient(135deg, rgba(255, 122, 24, 0.12), transparent 34%),
    linear-gradient(225deg, rgba(93, 214, 255, 0.12), transparent 36%),
    rgba(9, 17, 30, 0.9);
}

.showcase-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 16px;
  margin-bottom: 14px;
}

.showcase-header span {
  display: block;
  margin-bottom: 4px;
  color: var(--accent-cold);
  font-size: 0.76rem;
  font-weight: 850;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.showcase-header strong {
  font-size: 1.05rem;
}

.showcase-header a {
  padding: 9px 12px;
  border-radius: 999px;
  background: rgba(255, 122, 24, 0.16);
  color: var(--accent-soft);
  font-size: 0.78rem;
  font-weight: 850;
}

.main-preview {
  position: relative;
  display: block;
  overflow: hidden;
  border: 1px solid rgba(168, 180, 200, 0.18);
  border-radius: 18px;
  aspect-ratio: 16 / 9;
  background: #111827;
}

.main-preview img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.5s ease, filter 0.3s ease;
}

.main-preview:hover img {
  transform: scale(1.04);
  filter: saturate(1.08);
}

.preview-overlay {
  position: absolute;
  left: 18px;
  bottom: 18px;
  max-width: min(82%, 360px);
  padding: 14px 16px;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 16px;
  background: rgba(4, 8, 20, 0.78);
  backdrop-filter: blur(12px);
}

.preview-overlay span {
  display: block;
  margin-bottom: 6px;
  color: var(--accent-soft);
  font-size: 0.72rem;
  font-weight: 850;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.preview-overlay h2 {
  margin-bottom: 4px;
  font-size: 1.7rem;
}

.preview-overlay p {
  color: var(--accent-cold);
  font-weight: 800;
}

.mini-projects {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 12px;
  margin-top: 14px;
}

.mini-project {
  display: grid;
  grid-template-rows: auto auto 1fr;
  gap: 7px;
  min-height: 150px;
  padding: 10px;
  border: 1px solid rgba(168, 180, 200, 0.14);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.045);
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.mini-project:hover {
  transform: translateY(-4px);
  border-color: rgba(255, 184, 108, 0.32);
}

.mini-project img {
  width: 100%;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  border-radius: 11px;
}

.mini-project span {
  font-weight: 850;
}

.mini-project small {
  color: var(--muted);
  line-height: 1.35;
}

.profile-strip {
  display: flex;
  align-items: center;
  gap: 14px;
  padding: 14px;
}

.profile-strip img {
  width: 58px;
  height: 58px;
  border: 1px solid rgba(168, 180, 200, 0.18);
  border-radius: 16px;
  object-fit: cover;
  background: rgba(4, 8, 20, 0.8);
}

.profile-strip strong {
  display: block;
  margin-bottom: 4px;
}

.profile-strip p {
  color: var(--muted);
  line-height: 1.5;
}

@media (max-width: 1020px) {
  .hero {
    grid-template-columns: 1fr;
    min-height: auto;
  }

  h1 {
    max-width: 760px;
  }
}

@media (max-width: 680px) {
  .hero {
    gap: 28px;
    padding-top: 22px;
  }

  .eyebrow {
    font-size: 0.9rem;
    line-height: 1.35;
  }

  h1 {
    font-size: clamp(2.35rem, 12vw, 3.3rem);
  }

  .hero-actions {
    display: grid;
    grid-template-columns: 1fr;
  }

  .hero-metrics {
    grid-template-columns: 1fr;
  }

  .hero-metrics li {
    min-height: auto;
  }

  .showcase-panel {
    padding: 14px;
  }

  .showcase-header {
    align-items: flex-start;
    flex-direction: column;
  }

  .preview-overlay {
    left: 12px;
    right: 12px;
    bottom: 12px;
    max-width: none;
  }

  .preview-overlay h2 {
    font-size: 1.35rem;
  }

  .mini-projects {
    grid-template-columns: 1fr;
  }

  .mini-project {
    grid-template-columns: 112px 1fr;
    grid-template-rows: auto auto;
    align-items: center;
    min-height: auto;
  }

  .mini-project img {
    grid-row: 1 / span 2;
  }
}
</style>
