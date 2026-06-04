<script setup>
import ProjectCard from "./ProjectCard.vue";
import { projects } from "../data/projects";

const commercialProjects = projects.filter((project) => project.type === "commercial");
const productProjects = projects.filter((project) => project.featured);
const learningProjects = projects.filter((project) => project.type === "learning");
</script>

<template>
  <section id="projects" class="projects">
    <div class="projects-intro">
      <p class="section-kicker">Proyectos</p>
      <h2 class="section-title">Primero impacto visual, despues profundidad tecnica.</h2>
      <p class="section-subtitle">
        Las demos comerciales muestran criterio de producto y venta. Los proyectos full-stack
        muestran arquitectura, autenticacion, datos, dashboards y backend conectado.
      </p>
    </div>

    <div class="projects-subsection commercial-showcase">
      <div class="subsection-heading">
        <div>
          <p class="section-kicker">Demos comerciales</p>
          <h3 class="subsection-title">Barberia, restaurante y tienda de ropa listas para mostrar a clientes.</h3>
        </div>
        <p>
          Cada demo tiene identidad propia, flujo navegable, llamadas a WhatsApp y una primera pantalla
          pensada para vender en segundos.
        </p>
      </div>

      <div class="projects-grid commercial-grid">
        <ProjectCard
          v-for="project in commercialProjects"
          :key="project.title"
          :project="project"
        />
      </div>
    </div>

    <div class="projects-subsection product-lab">
      <div class="subsection-heading">
        <div>
          <p class="section-kicker">Full-stack</p>
          <h3 class="subsection-title">Productos con datos, roles, APIs y deploy.</h3>
        </div>
        <p>
          Este bloque suma evidencia tecnica sin robarle foco a las demos comerciales:
          autenticacion, roles, persistencia, dashboards y backend conectado.
        </p>
      </div>

      <div class="projects-grid product-grid">
        <ProjectCard
          v-for="project in productProjects"
          :key="project.title"
          :project="project"
        />
      </div>
    </div>

    <div class="projects-subsection foundation-lab">
      <div class="subsection-heading">
        <div>
          <p class="section-kicker">Fundamentos</p>
          <h3 class="subsection-title">Bases de frontend que completan la evolucion.</h3>
        </div>
        <p>
          Proyectos mas simples para mostrar consumo de APIs, logica de interfaz,
          estado, filtros y persistencia local.
        </p>
      </div>

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
.projects {
  width: min(1320px, calc(100% - 48px));
}

.projects-intro {
  max-width: 900px;
}

.projects-subsection {
  margin-top: 38px;
}

.subsection-heading {
  display: grid;
  grid-template-columns: minmax(0, 0.9fr) minmax(280px, 0.55fr);
  gap: 24px;
  align-items: end;
  margin-bottom: 22px;
}

.subsection-heading p:last-child {
  color: var(--muted);
  line-height: 1.7;
}

.subsection-title {
  font-size: clamp(1.45rem, 1.1vw + 1rem, 2.2rem);
  line-height: 1.08;
}

.projects-grid {
  display: grid;
  gap: 18px;
}

.commercial-showcase,
.product-lab,
.foundation-lab {
  padding: 28px;
  border: 1px solid rgba(255, 255, 255, 0.13);
  border-radius: 28px;
  overflow: hidden;
}

.commercial-showcase {
  background:
    linear-gradient(135deg, rgba(255, 107, 53, 0.13), transparent 34%),
    linear-gradient(225deg, rgba(255, 209, 102, 0.11), transparent 36%),
    rgba(255, 255, 255, 0.035);
}

.product-lab {
  background:
    linear-gradient(135deg, rgba(77, 216, 255, 0.11), transparent 34%),
    linear-gradient(225deg, rgba(85, 239, 196, 0.08), transparent 36%),
    rgba(255, 255, 255, 0.025);
}

.foundation-lab {
  background:
    linear-gradient(135deg, rgba(255, 92, 138, 0.1), transparent 34%),
    rgba(255, 255, 255, 0.02);
}

.commercial-grid {
  grid-template-columns: repeat(3, minmax(0, 1fr));
}

.product-grid {
  grid-template-columns: repeat(4, minmax(0, 1fr));
}

.secondary-grid {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}

.commercial-grid :deep(.project-card) {
  min-height: 100%;
}

.product-grid :deep(.project-card) {
  padding: 20px;
}

.product-grid :deep(.description) {
  font-size: 0.95rem;
}

.secondary-grid :deep(.project-card) {
  min-height: 100%;
}

@media (max-width: 1120px) {
  .commercial-grid,
  .product-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 760px) {
  .projects {
    width: min(100% - 28px, 1320px);
  }

  .subsection-heading,
  .commercial-grid,
  .product-grid,
  .secondary-grid {
    grid-template-columns: 1fr;
  }

  .commercial-showcase,
  .product-lab,
  .foundation-lab {
    padding: 16px;
    border-radius: 22px;
  }
}
</style>
