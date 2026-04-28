<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";

const featuredProjects = projects.filter((project) => project.featured);
const learningProjects = projects.filter((project) => !project.featured);
</script>

<template>
  <section id="projects" class="projects">
    <p class="section-kicker">Proyectos</p>
    <h2 class="section-title">Trabajo real para mostrar cómo pienso, construyo y resuelvo.</h2>

    <p class="section-subtitle">
      Estos proyectos resumen mi etapa actual: aplicaciones conectadas a APIs, autenticación,
      lógica de negocio, persistencia y deploy. Cada uno me ayudó a practicar una parte distinta del proceso completo.
    </p>

    <div class="projects-grid">
      <ProjectCard
        v-for="project in featuredProjects"
        :key="project.title"
        :project="project"
      />
    </div>

    <div class="projects-subsection">
      <p class="section-kicker">Otros proyectos</p>
      <h3 class="subsection-title">Proyectos clave de aprendizaje y evolución técnica.</h3>
      <p class="section-subtitle subsection-copy">
        También mantengo visibles algunos proyectos más chicos porque muestran cómo fui consolidando
        fundamentos de interfaz, consumo de APIs y lógica en frontend.
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
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 22px;
}

.projects-subsection {
  margin-top: 44px;
}

.subsection-title {
  font-size: clamp(1.35rem, 1vw + 1rem, 2rem);
  margin-bottom: 12px;
}

.subsection-copy {
  margin-bottom: 28px;
}

.secondary-grid :deep(.project-card) {
  padding: 24px;
}

@media (max-width: 900px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>
