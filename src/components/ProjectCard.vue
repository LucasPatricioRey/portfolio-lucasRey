<script setup>
defineProps({
  project: {
    type: Object,
    required: true
  }
});
</script>

<template>
  <article class="project-card glass-panel" :class="{ featured: project.featured }">
    <a
      class="preview-frame"
      :href="project.demo"
      target="_blank"
      rel="noopener noreferrer"
      :aria-label="`Abrir demo de ${project.title}`"
    >
      <img
        v-if="project.preview"
        :src="project.preview"
        :alt="`Vista previa de ${project.title}`"
      >
      <div v-else class="preview-placeholder">
        <span>{{ project.title }}</span>
        <small>{{ project.category }}</small>
      </div>
    </a>

    <div class="card-top">
      <div>
        <span class="eyebrow">{{ project.eyebrow }}</span>
        <h3>{{ project.title }}</h3>
      </div>
      <p class="category">{{ project.category }}</p>
    </div>

    <p class="description">{{ project.description }}</p>

    <div class="techs">
      <span v-for="tech in project.technologies" :key="tech">
        {{ tech }}
      </span>
    </div>

    <div class="links">
      <a :href="project.demo" target="_blank" rel="noopener noreferrer">Ver demo</a>
      <a :href="project.github" target="_blank" rel="noopener noreferrer" class="secondary-link">Repositorio</a>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 28px;
  border-radius: 28px;
  border: 1px solid var(--line);
  transition: transform 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease;
}

.project-card:hover {
  transform: translateY(-6px);
  border-color: rgba(255, 184, 108, 0.38);
  box-shadow: 0 24px 60px rgba(0, 0, 0, 0.28);
}

.featured {
  background:
    radial-gradient(circle at top right, rgba(255, 122, 24, 0.16), transparent 32%),
    rgba(10, 18, 32, 0.82);
}

.preview-frame {
  display: block;
  overflow: hidden;
  border-radius: 18px;
  border: 1px solid rgba(168, 180, 200, 0.14);
  background: rgba(255, 255, 255, 0.04);
  aspect-ratio: 16 / 9;
}

.preview-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.25s ease;
}

.preview-placeholder {
  width: 100%;
  height: 100%;
  display: grid;
  place-content: center;
  gap: 8px;
  padding: 20px;
  text-align: center;
  background:
    radial-gradient(circle at top right, rgba(255, 122, 24, 0.22), transparent 30%),
    radial-gradient(circle at bottom left, rgba(93, 214, 255, 0.18), transparent 28%),
    linear-gradient(135deg, rgba(11, 23, 41, 0.95), rgba(7, 17, 31, 0.9));
}

.preview-placeholder span {
  font-size: 1.35rem;
  font-weight: 800;
  color: var(--text);
}

.preview-placeholder small {
  color: var(--muted);
  font-size: 0.88rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.project-card:hover .preview-frame img {
  transform: scale(1.03);
}

.card-top {
  display: flex;
  justify-content: space-between;
  gap: 16px;
}

.eyebrow {
  display: inline-block;
  margin-bottom: 12px;
  color: var(--accent-soft);
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

h3 {
  font-size: 1.7rem;
}

.category {
  color: var(--accent-cold);
  font-size: 0.9rem;
  font-weight: 800;
  white-space: nowrap;
}

.description {
  color: var(--muted);
  line-height: 1.8;
}

.techs {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.techs span {
  padding: 8px 10px;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(168, 180, 200, 0.14);
  color: #e5eef8;
  font-size: 0.9rem;
  font-weight: 700;
}

.links {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: auto;
}

.links a {
  padding: 12px 16px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--accent), #ff9a3c);
  color: #081120;
  font-weight: 800;
}

.secondary-link {
  background: transparent !important;
  border: 1px solid rgba(168, 180, 200, 0.2);
  color: var(--text) !important;
}

@media (max-width: 640px) {
  .card-top {
    flex-direction: column;
  }

  .category {
    white-space: normal;
  }
}
</style>
