<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";

const featuredCase = projects.find((project) => project.title === "REDO") ?? projects[0];
const productProjects = projects.filter((project) => project.featured && project.title !== featuredCase.title);
const learningProjects = projects.filter((project) => !project.featured);
</script>

<template>
  <section id="projects" class="projects">
    <p class="section-kicker">Proyectos</p>
    <h2 class="section-title">No son demos sueltas: son productos web con flujo, datos y deploy.</h2>

    <p class="section-subtitle">
      Primero aparece el producto mas fuerte y despues el resto del stack aplicado:
      autenticacion, roles, APIs, persistencia, dashboards y despliegue.
    </p>

    <article id="featured-project" class="featured-case glass-panel">
      <a
        class="case-preview"
        :href="featuredCase.demo"
        target="_blank"
        rel="noopener noreferrer"
        :aria-label="`Abrir demo de ${featuredCase.title}`"
      >
        <img :src="featuredCase.preview" :alt="`Vista previa de ${featuredCase.title}`" loading="lazy">
        <span>Producto real</span>
      </a>

      <div class="case-content">
        <p class="case-label">Caso destacado</p>
        <h3>{{ featuredCase.title }}</h3>
        <p class="case-description">{{ featuredCase.description }}</p>

        <ul class="case-points">
          <li v-for="item in featuredCase.highlights" :key="item">{{ item }}</li>
        </ul>

        <div class="case-stack" aria-label="Stack del proyecto destacado">
          <span v-for="tech in featuredCase.technologies" :key="tech">{{ tech }}</span>
        </div>

        <div class="case-links">
          <a :href="featuredCase.demo" target="_blank" rel="noopener noreferrer">Abrir demo</a>
          <a :href="featuredCase.github" target="_blank" rel="noopener noreferrer" class="secondary-link">
            Ver codigo
          </a>
        </div>
      </div>
    </article>

    <div class="projects-subsection">
      <p class="section-kicker">Productos</p>
      <h3 class="subsection-title">Mas proyectos full-stack para revisar en profundidad.</h3>

      <div class="projects-grid">
        <ProjectCard
          v-for="project in productProjects"
          :key="project.title"
          :project="project"
        />
      </div>
    </div>

    <div class="projects-subsection">
      <p class="section-kicker">Base tecnica</p>
      <h3 class="subsection-title">Proyectos de aprendizaje que muestran fundamentos.</h3>
      <p class="section-subtitle subsection-copy">
        Los mantengo visibles porque muestran evolucion en interfaz, consumo de APIs,
        logica de frontend y persistencia local.
      </p>

      <div class="projects-grid secondary-grid">
        <ProjectCard
          v-for="project in learningProjects"
          :key="project.title"
          :project="project"
        />
      </div>
    </div>
  </section>
</template>

<style scoped>
.featured-case {
  display: grid;
  grid-template-columns: minmax(0, 1.05fr) minmax(320px, 0.95fr);
  gap: 28px;
  align-items: center;
  padding: 26px;
  border-radius: 28px;
  scroll-margin-top: 130px;
  background:
    linear-gradient(135deg, rgba(255, 122, 24, 0.14), transparent 34%),
    linear-gradient(225deg, rgba(54, 211, 153, 0.08), transparent 36%),
    rgba(10, 18, 32, 0.86);
}

.case-preview {
  position: relative;
  display: block;
  overflow: hidden;
  border: 1px solid rgba(168, 180, 200, 0.16);
  border-radius: 22px;
  aspect-ratio: 16 / 10;
  background: #111827;
}

.case-preview img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.45s ease, filter 0.3s ease;
}

.case-preview:hover img {
  transform: scale(1.04);
  filter: saturate(1.08);
}

.case-preview span {
  position: absolute;
  left: 16px;
  top: 16px;
  padding: 9px 13px;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 999px;
  background: rgba(4, 8, 20, 0.78);
  color: var(--accent-soft);
  font-size: 0.76rem;
  font-weight: 850;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  backdrop-filter: blur(12px);
}

.case-label {
  margin-bottom: 12px;
  color: var(--accent-green);
  font-size: 0.78rem;
  font-weight: 850;
  letter-spacing: 0.14em;
  text-transform: uppercase;
}

.case-content h3 {
  margin-bottom: 14px;
  font-size: clamp(2rem, 2.4vw, 3.1rem);
}

.case-description {
  color: var(--muted);
  line-height: 1.8;
  font-size: 1.04rem;
}

.case-points {
  display: grid;
  gap: 10px;
  margin: 20px 0;
  list-style: none;
}

.case-points li {
  position: relative;
  padding-left: 22px;
  color: #d9e5f2;
  line-height: 1.6;
}

.case-points li::before {
  content: "";
  position: absolute;
  left: 0;
  top: 10px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--accent-green);
}

.case-stack,
.case-links {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.case-stack {
  margin-bottom: 24px;
}

.case-stack span {
  padding: 8px 10px;
  border: 1px solid rgba(93, 214, 255, 0.18);
  border-radius: 999px;
  background: rgba(93, 214, 255, 0.08);
  color: #dff8ff;
  font-size: 0.88rem;
  font-weight: 800;
}

.case-links a {
  padding: 12px 16px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--accent), #ffb15f);
  color: #081120;
  font-weight: 850;
  transition: transform 0.2s ease, box-shadow 0.25s ease;
}

.case-links a:hover {
  transform: translateY(-2px);
  box-shadow: 0 14px 28px rgba(255, 122, 24, 0.2);
}

.case-links .secondary-link {
  background: transparent;
  border: 1px solid rgba(168, 180, 200, 0.24);
  color: var(--text);
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 22px;
}

.projects-subsection {
  margin-top: 46px;
}

.subsection-title {
  margin-bottom: 22px;
  font-size: clamp(1.35rem, 1vw + 1rem, 2rem);
}

.subsection-copy {
  margin-bottom: 28px;
}

.secondary-grid {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}

.secondary-grid :deep(.project-card) {
  padding: 24px;
}

@media (max-width: 980px) {
  .featured-case,
  .projects-grid,
  .secondary-grid {
    grid-template-columns: 1fr;
  }
}

@media (max-width: 640px) {
  .featured-case {
    padding: 16px;
    border-radius: 22px;
    scroll-margin-top: 110px;
  }

  .case-preview {
    border-radius: 16px;
  }
}
</style>
