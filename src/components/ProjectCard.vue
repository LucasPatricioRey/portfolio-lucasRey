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
      <span class="preview-badge">{{ project.featured ? "Destacado" : "Evolucion" }}</span>

      <img
        v-if="project.preview"
        :src="project.preview"
        :alt="`Vista previa de ${project.title}`"
      >

      <div v-else class="preview-placeholder">
        <span>{{ project.title }}</span>
        <small>{{ project.category }}</small>
      </div>

      <div class="preview-cta">
        <span>Explorar proyecto</span>
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
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 20px;
  padding: 28px;
  border-radius: 28px;
  border: 1px solid var(--line);
  overflow: hidden;
  transition: transform 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease;
}

.project-card:hover {
  transform:
    perspective(1200px)
    rotateX(var(--tilt-x, 0deg))
    rotateY(var(--tilt-y, 0deg))
    translateY(-14px)
    scale(1.015);
  border-color: rgba(255, 184, 108, 0.38);
  box-shadow: 0 34px 84px rgba(0, 0, 0, 0.38);
}

.featured {
  background:
    radial-gradient(circle at top right, rgba(255, 122, 24, 0.24), transparent 32%),
    radial-gradient(circle at bottom left, rgba(93, 214, 255, 0.16), transparent 28%),
    rgba(10, 18, 32, 0.82);
  animation: accentPulse 4.8s ease-in-out infinite;
}

.project-card::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1px;
  background: linear-gradient(
    135deg,
    rgba(255, 255, 255, 0.12),
    rgba(255, 122, 24, 0.22),
    rgba(93, 214, 255, 0.18)
  );
  -webkit-mask:
    linear-gradient(#fff 0 0) content-box,
    linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  opacity: 0;
  transition: opacity 0.25s ease;
  pointer-events: none;
}

.project-card:hover::before {
  opacity: 1;
}

.preview-frame {
  position: relative;
  display: block;
  overflow: hidden;
  border-radius: 18px;
  border: 1px solid rgba(168, 180, 200, 0.14);
  background: rgba(255, 255, 255, 0.04);
  aspect-ratio: 16 / 9;
}

.preview-badge {
  position: absolute;
  top: 14px;
  left: 14px;
  z-index: 2;
  padding: 8px 12px;
  border-radius: 999px;
  background: rgba(5, 11, 24, 0.72);
  border: 1px solid rgba(255, 255, 255, 0.16);
  color: #f7fbff;
  font-size: 0.72rem;
  font-weight: 800;
  letter-spacing: 0.14em;
  text-transform: uppercase;
  backdrop-filter: blur(12px);
}

.preview-frame img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  display: block;
  transition: transform 0.45s cubic-bezier(0.22, 1, 0.36, 1), filter 0.3s ease;
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
  transform: scale(1.1);
  filter: saturate(1.12);
}

.preview-frame::after {
  content: "";
  position: absolute;
  inset: auto 0 0;
  height: 58%;
  background: linear-gradient(180deg, transparent, rgba(4, 8, 20, 0.42));
  pointer-events: none;
}

.preview-frame::before {
  content: "";
  position: absolute;
  inset: -20% auto auto -30%;
  width: 42%;
  height: 160%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.18), transparent);
  transform: rotate(14deg) translateX(-140%);
  transition: transform 0.7s cubic-bezier(0.22, 1, 0.36, 1);
  z-index: 1;
  pointer-events: none;
}

.project-card:hover .preview-frame::before {
  transform: rotate(14deg) translateX(360%);
}

.preview-cta {
  position: absolute;
  inset: auto 16px 16px auto;
  z-index: 2;
  transform: translateY(10px);
  opacity: 0;
  transition: transform 0.25s ease, opacity 0.25s ease;
}

.preview-cta span {
  display: inline-flex;
  align-items: center;
  gap: 8px;
  padding: 10px 14px;
  border-radius: 999px;
  background: rgba(255, 122, 24, 0.92);
  color: #07111f;
  font-size: 0.82rem;
  font-weight: 800;
  box-shadow: 0 16px 30px rgba(255, 122, 24, 0.28);
}

.preview-cta span::after {
  content: "↗";
  font-size: 0.92rem;
}

.project-card:hover .preview-cta {
  opacity: 1;
  transform: translateY(0);
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
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.project-card:hover .techs span {
  transform: translateY(-2px);
  border-color: rgba(255, 184, 108, 0.2);
  background: rgba(255, 255, 255, 0.06);
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
  transition: transform 0.2s ease, box-shadow 0.25s ease;
}

.links a:hover {
  transform: translateY(-2px);
  box-shadow: 0 14px 28px rgba(255, 122, 24, 0.2);
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
