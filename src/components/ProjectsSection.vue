<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";
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
        v-for="project in projects"
        :key="project.title"
        :project="project"
      />
    </div>
  </section>
</template>

<style scoped>
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 22px;
}

@media (max-width: 900px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>