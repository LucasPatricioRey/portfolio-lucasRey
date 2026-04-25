<script setup>
defineProps({
  project: {
    type: Object,
    required: true
  }
});
</script>

<template>
  <article class="project-card" :class="{ featured: project.featured }">
    <span v-if="project.featured" class="badge">Proyecto destacado</span>

    <h3>{{ project.title }}</h3>

    <p class="type" v-if="project.featured">Full Stack Project</p>
    <p class="type" v-else>Portfolio Project</p>

    <p class="description">{{ project.description }}</p>

    <div class="techs">
      <span v-for="tech in project.technologies" :key="tech">
        {{ tech }}
      </span>
    </div>

    <div class="links">
      <a :href="project.demo" target="_blank" rel="noopener noreferrer">Demo</a>
      <a :href="project.github" target="_blank" rel="noopener noreferrer">GitHub</a>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  background: #0f172a;
  border: 1px solid rgba(148, 163, 184, 0.15);
  padding: 24px;
  border-radius: 22px;
  transition: 0.2s ease;
}

.project-card:hover {
  transform: translateY(-6px) scale(1.01);
  box-shadow: 0 20px 50px rgba(0, 0, 0, 0.35);
  border-color: rgba(56, 189, 248, 0.45);
}

.featured {
  background:
    radial-gradient(circle at top right, rgba(56, 189, 248, 0.12), transparent 35%),
    #0f172a;
}

.badge {
  display: inline-block;
  color: #38bdf8;
  font-weight: 800;
  margin-bottom: 14px;
}

h3 {
  font-size: 24px;
  margin-bottom: 8px;
}

.type {
  color: #38bdf8;
  font-weight: 700;
  margin-bottom: 10px;
  font-size: 14px;
}

.description {
  color: #94a3b8;
  line-height: 1.7;
  margin-bottom: 18px;
}

.techs {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-bottom: 22px;
}

.techs span {
  background: #020617;
  color: #cbd5e1;
  padding: 7px 10px;
  border-radius: 999px;
  font-size: 13px;
  font-weight: 700;
}

.links {
  display: flex;
  gap: 10px;
}

.links a {
  background: #2563eb;
  color: white;
  padding: 10px 14px;
  border-radius: 10px;
  font-weight: 800;
}

.links a:last-child {
  background: transparent;
  border: 1px solid #334155;
}
</style>
