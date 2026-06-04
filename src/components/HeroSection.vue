<script setup>
import { projects } from "../data/projects";

const commercialProjects = projects.filter((project) => project.type === "commercial");

const proofPoints = [
  { value: "3", label: "demos comerciales listas para vender" },
  { value: "9", label: "proyectos publicados y navegables" },
  { value: "Full", label: "frontend, backend, datos y deploy" }
];
</script>

<template>
  <section id="home" class="hero">
    <div class="hero-grid">
      <div class="hero-copy">
        <p class="eyebrow">Portfolio vivo de Lucas Rey</p>

        <h1>
          Interfaces que se ven fuertes, funcionan y ya estan deployadas.
        </h1>

        <p class="intro">
          Frontend junior con base full-stack. Construyo landings comerciales,
          apps con autenticacion, paneles, APIs, MongoDB y experiencias pensadas
          para que un cliente real pueda usarlas, probarlas y comprarlas.
        </p>

        <div class="hero-actions" aria-label="Acciones principales">
          <a href="#demos" class="btn btn-primary">Ver demos comerciales</a>
          <a href="#flow" class="btn btn-secondary">Ver flujo de trabajo</a>
          <a href="/cv-lucas-rey.pdf" class="btn btn-ghost" download>Descargar CV</a>
        </div>

        <ul class="hero-metrics" aria-label="Resumen rapido">
          <li v-for="point in proofPoints" :key="point.label">
            <strong>{{ point.value }}</strong>
            <span>{{ point.label }}</span>
          </li>
        </ul>
      </div>

      <div class="hero-portrait">
        <div class="portrait-stage">
          <picture>
            <source srcset="/lucas-rey-photo.webp" type="image/webp">
            <img src="/lucas-rey-photo.png" alt="Retrato de Lucas Rey" fetchpriority="high">
          </picture>

          <div class="portrait-caption">
            <span>Lucas Rey</span>
            <strong>Frontend junior + producto web</strong>
          </div>

          <div class="portrait-signal signal-top">
            <span>Deploy</span>
            <strong>Vercel + APIs</strong>
          </div>

          <div class="portrait-signal signal-bottom">
            <span>Stack</span>
            <strong>Vue, React, Node, MongoDB</strong>
          </div>
        </div>
      </div>
    </div>

    <div id="demos" class="hero-showroom" aria-label="Demos comerciales destacadas">
      <a
        v-for="project in commercialProjects"
        :key="project.title"
        class="demo-tile"
        :href="project.demo"
        target="_blank"
        rel="noopener noreferrer"
      >
        <img :src="project.preview" :alt="`Vista previa de ${project.title}`" loading="lazy">
        <div class="demo-content">
          <span>{{ project.category }}</span>
          <strong>{{ project.title }}</strong>
          <small>{{ project.description }}</small>
        </div>
      </a>
    </div>
  </section>
</template>

<style scoped>
.hero {
  width: min(1440px, calc(100% - 32px));
  min-height: calc(100svh - 24px);
  display: grid;
  align-content: center;
  gap: 28px;
  padding: 34px 0 64px;
}

.hero-grid {
  position: relative;
  display: grid;
  grid-template-columns: minmax(0, 0.92fr) minmax(380px, 1.08fr);
  align-items: center;
  gap: 40px;
  min-height: min(760px, calc(100svh - 190px));
  padding: clamp(22px, 3vw, 48px);
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 28px;
  overflow: hidden;
  background:
    linear-gradient(120deg, rgba(255, 107, 53, 0.16), transparent 34%),
    linear-gradient(240deg, rgba(77, 216, 255, 0.13), transparent 32%),
    linear-gradient(180deg, rgba(255, 255, 255, 0.055), rgba(255, 255, 255, 0.025)),
    rgba(12, 9, 18, 0.78);
  box-shadow: 0 36px 120px rgba(0, 0, 0, 0.44);
}

.hero-grid::before {
  content: "";
  position: absolute;
  inset: 0;
  background:
    linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.08), transparent),
    repeating-linear-gradient(90deg, rgba(255, 255, 255, 0.055) 0 1px, transparent 1px 12vw);
  transform: translateX(-100%);
  animation: heroSweep 7.5s ease-in-out infinite;
  pointer-events: none;
}

.hero-grid::after {
  content: "";
  position: absolute;
  inset: auto 0 0;
  height: 36%;
  background:
    linear-gradient(180deg, transparent, rgba(85, 239, 196, 0.06)),
    linear-gradient(90deg, rgba(255, 107, 53, 0.12), transparent, rgba(77, 216, 255, 0.12));
  pointer-events: none;
}

.hero-copy,
.hero-portrait {
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
  border: 1px solid rgba(85, 239, 196, 0.26);
  border-radius: 999px;
  background: rgba(85, 239, 196, 0.08);
  color: #c9fff0;
  font-weight: 850;
}

.eyebrow::before {
  content: "";
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: var(--accent-green);
  box-shadow: 0 0 24px rgba(85, 239, 196, 0.75);
}

h1 {
  max-width: 13ch;
  margin-bottom: 22px;
  font-size: clamp(3rem, 5.6vw, 6.2rem);
  line-height: 0.93;
}

.intro {
  max-width: 650px;
  color: var(--muted);
  line-height: 1.78;
  font-size: clamp(1rem, 0.35vw + 0.98rem, 1.18rem);
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin: 28px 0 26px;
}

.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  min-height: 50px;
  padding: 13px 18px;
  border-radius: 13px;
  font-weight: 900;
  transition: transform 0.22s ease, border-color 0.22s ease, background 0.22s ease, box-shadow 0.25s ease;
}

.btn:hover {
  transform: translateY(-3px);
}

.btn-primary {
  background: linear-gradient(135deg, var(--accent), var(--accent-soft));
  color: #120b08;
  box-shadow: 0 20px 48px rgba(255, 107, 53, 0.26);
}

.btn-secondary {
  border: 1px solid rgba(77, 216, 255, 0.28);
  background: rgba(77, 216, 255, 0.1);
  color: #e4faff;
}

.btn-ghost {
  border: 1px solid rgba(255, 255, 255, 0.18);
  color: var(--text);
}

.hero-metrics {
  list-style: none;
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 12px;
}

.hero-metrics li {
  min-height: 104px;
  padding: 18px;
  border: 1px solid rgba(255, 255, 255, 0.13);
  border-radius: 18px;
  background: rgba(255, 255, 255, 0.055);
}

.hero-metrics strong {
  display: block;
  margin-bottom: 8px;
  color: var(--accent-soft);
  font-size: clamp(1.4rem, 1vw + 1rem, 2rem);
  line-height: 1;
}

.hero-metrics span {
  color: var(--muted);
  font-size: 0.92rem;
  line-height: 1.35;
}

.hero-portrait {
  min-height: 640px;
  display: grid;
  place-items: center;
}

.portrait-stage {
  position: relative;
  width: min(100%, 620px);
  isolation: isolate;
  animation: portraitEnter 900ms cubic-bezier(0.22, 1, 0.36, 1) both;
}

.portrait-stage::before,
.portrait-stage::after {
  content: "";
  position: absolute;
  z-index: -1;
  border: 1px solid rgba(255, 255, 255, 0.13);
  pointer-events: none;
}

.portrait-stage::before {
  inset: 8% -6% 10% 8%;
  border-radius: 30px;
  background:
    linear-gradient(135deg, rgba(255, 107, 53, 0.18), transparent),
    rgba(255, 255, 255, 0.04);
  transform: rotate(4deg);
}

.portrait-stage::after {
  inset: 18% 8% -6% -6%;
  border-radius: 28px;
  background:
    linear-gradient(135deg, rgba(77, 216, 255, 0.16), transparent),
    rgba(85, 239, 196, 0.045);
  transform: rotate(-5deg);
}

.portrait-stage picture {
  display: block;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 30px;
  background: #0f0c14;
  box-shadow: 0 36px 96px rgba(0, 0, 0, 0.48);
  transform: rotate(-1.4deg);
}

.portrait-stage img {
  width: 100%;
  height: min(70svh, 680px);
  min-height: 560px;
  object-fit: cover;
  object-position: center 16%;
  filter: saturate(1.06) contrast(1.02);
}

.portrait-caption,
.portrait-signal {
  position: absolute;
  z-index: 2;
  border: 1px solid rgba(255, 255, 255, 0.18);
  background: rgba(10, 8, 16, 0.82);
  backdrop-filter: blur(16px);
  box-shadow: 0 24px 56px rgba(0, 0, 0, 0.32);
}

.portrait-caption {
  left: -18px;
  bottom: 28px;
  max-width: 310px;
  padding: 18px 20px;
  border-radius: 20px;
}

.portrait-caption span,
.portrait-signal span {
  display: block;
  margin-bottom: 5px;
  color: var(--accent-cold);
  font-size: 0.78rem;
  font-weight: 900;
  text-transform: uppercase;
}

.portrait-caption strong {
  font-size: clamp(1.2rem, 1.1vw + 1rem, 1.85rem);
  line-height: 1.08;
}

.portrait-signal {
  padding: 13px 15px;
  border-radius: 16px;
  animation: floatPanel 4.8s ease-in-out infinite;
}

.portrait-signal strong {
  display: block;
  max-width: 190px;
  line-height: 1.25;
}

.signal-top {
  top: 44px;
  right: -12px;
}

.signal-bottom {
  right: 16px;
  bottom: 80px;
  animation-delay: 1.2s;
}

.hero-showroom {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 14px;
}

.demo-tile {
  position: relative;
  min-height: 250px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 22px;
  background: rgba(16, 12, 22, 0.76);
  box-shadow: 0 24px 70px rgba(0, 0, 0, 0.28);
  transition: transform 0.24s ease, border-color 0.24s ease, box-shadow 0.24s ease;
}

.demo-tile:hover {
  transform: translateY(-8px);
  border-color: rgba(255, 209, 102, 0.36);
  box-shadow: 0 34px 86px rgba(0, 0, 0, 0.4);
}

.demo-tile img {
  width: 100%;
  height: 100%;
  min-height: 250px;
  object-fit: cover;
  transition: transform 0.55s cubic-bezier(0.22, 1, 0.36, 1), filter 0.3s ease;
}

.demo-tile:hover img {
  transform: scale(1.06);
  filter: saturate(1.12);
}

.demo-tile::after {
  content: "";
  position: absolute;
  inset: 35% 0 0;
  background: linear-gradient(180deg, transparent, rgba(7, 6, 11, 0.92));
  pointer-events: none;
}

.demo-content {
  position: absolute;
  left: 18px;
  right: 18px;
  bottom: 18px;
  z-index: 1;
}

.demo-content span {
  display: inline-flex;
  margin-bottom: 8px;
  padding: 7px 10px;
  border: 1px solid rgba(255, 255, 255, 0.15);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.09);
  color: #fff6dd;
  font-size: 0.75rem;
  font-weight: 900;
}

.demo-content strong {
  display: block;
  margin-bottom: 7px;
  font-size: clamp(1.3rem, 1vw + 1rem, 1.8rem);
}

.demo-content small {
  display: -webkit-box;
  overflow: hidden;
  color: rgba(255, 255, 255, 0.78);
  line-height: 1.45;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
}

@keyframes heroSweep {
  0%,
  42% {
    transform: translateX(-105%);
    opacity: 0;
  }

  55% {
    opacity: 1;
  }

  72%,
  100% {
    transform: translateX(105%);
    opacity: 0;
  }
}

@keyframes portraitEnter {
  from {
    opacity: 0;
    transform: translateY(34px) scale(0.96);
  }

  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

@keyframes floatPanel {
  0%,
  100% {
    transform: translate3d(0, 0, 0);
  }

  50% {
    transform: translate3d(0, -12px, 0);
  }
}

@media (max-width: 1120px) {
  .hero-grid {
    grid-template-columns: 1fr;
    min-height: auto;
  }

  h1 {
    max-width: 760px;
  }

  .hero-portrait {
    min-height: auto;
  }

  .portrait-stage {
    width: min(100%, 560px);
  }
}

@media (max-width: 820px) {
  .hero {
    width: min(100% - 20px, 1440px);
    min-height: auto;
    padding-top: 20px;
  }

  .hero-grid {
    gap: 26px;
    padding: 18px;
    border-radius: 22px;
  }

  h1 {
    font-size: clamp(2.65rem, 12.5vw, 4.2rem);
  }

  .hero-actions,
  .hero-metrics,
  .hero-showroom {
    grid-template-columns: 1fr;
  }

  .hero-actions {
    display: grid;
  }

  .hero-metrics li {
    min-height: auto;
  }

  .portrait-stage img {
    height: auto;
    min-height: 0;
    aspect-ratio: 4 / 5;
  }

  .portrait-caption {
    left: 12px;
    right: 12px;
    bottom: 14px;
    max-width: none;
  }

  .portrait-signal {
    position: relative;
    inset: auto;
    display: inline-block;
    margin-top: 10px;
    margin-right: 8px;
    animation: none;
  }

  .signal-bottom {
    right: auto;
    bottom: auto;
  }

  .demo-tile,
  .demo-tile img {
    min-height: 230px;
  }
}
</style>
