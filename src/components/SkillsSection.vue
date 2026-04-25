<script setup>
import { skillGroups } from "../data/skills";
</script>

<template>
  <section id="skills" class="skills">
    <p class="section-kicker">Stack</p>
    <h2 class="section-title">Tecnologías con las que ya construyo proyectos completos.</h2>

    <p class="section-subtitle">
      Este stack refleja lo que hoy puedo llevar a la práctica: interfaces, lógica de servidor,
      autenticación, base de datos y despliegue para dejar proyectos funcionando de verdad.
    </p>

    <div class="skills-grid">
      <article v-for="group in skillGroups" :key="group.title" class="glass-panel skill-card">
        <h3>{{ group.title }}</h3>
        <p>{{ group.description }}</p>

        <div class="skill-items">
          <span v-for="item in group.items" :key="item">
            {{ item }}
          </span>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
}

.skill-card {
  padding: 28px;
  border-radius: 26px;
}

.skill-card h3 {
  margin-bottom: 12px;
  font-size: 1.4rem;
}

.skill-card p {
  min-height: 86px;
  margin-bottom: 20px;
  color: var(--muted);
  line-height: 1.8;
}

.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.skill-items span {
  padding: 10px 12px;
  border-radius: 999px;
  background: rgba(93, 214, 255, 0.08);
  border: 1px solid rgba(93, 214, 255, 0.16);
  color: #e7f9ff;
  font-weight: 700;
}

@media (max-width: 920px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }

  .skill-card p {
    min-height: auto;
  }
}
</style>