<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";
</script>

<template>
  <section id="projects" class="projects">
    <h2 class="section-title">Proyectos</h2>

    <p class="section-subtitle">
      Algunos proyectos desarrollados durante mi formación, enfocados en frontend,
      backend, consumo de APIs, autenticación, bases de datos y deploy.
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
.projects {
  background: #020617;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 22px;
}

@media (max-width: 850px) {
  .projects-grid {
    grid-template-columns: 1fr;
  }
}
</style>