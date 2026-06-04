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
      <span class="preview-badge">{{ project.featured ? "Producto" : "Base tecnica" }}</span>

      <img
        v-if="project.preview"
        :src="project.preview"
        :alt="`Vista previa de ${project.title}`"
        loading="lazy"
      >

      <div v-else class="preview-placeholder">
        <span>{{ project.title }}</span>
        <small>{{ project.category }}</small>
      </div>

      <div class="preview-cta">
        <span>Explorar</span>
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

    <ul v-if="project.highlights?.length" class="highlights">
      <li v-for="item in project.highlights.slice(0, 2)" :key="item">{{ item }}</li>
    </ul>

    <div class="techs">
      <span v-for="tech in project.technologies" :key="tech">
        {{ tech }}
      </span>
    </div>

    <div class="links">
      <a :href="project.demo" target="_blank" rel="noopener noreferrer">Demo</a>
      <a :href="project.github" target="_blank" rel="noopener noreferrer" class="secondary-link">Codigo</a>
    </div>
  </article>
</template>

<style scoped>
.project-card {
  position: relative;
  display: flex;
  flex-direction: column;
  gap: 18px;
  padding: 24px;
  border: 1px solid var(--line);
  border-radius: 22px;
  overflow: hidden;
  transition: transform 0.2s ease, border-color 0.2s ease, box-shadow 0.2s ease;
}

.project-card:hover {
  transform:
    perspective(1200px)
    rotateX(var(--tilt-x, 0deg))
    rotateY(var(--tilt-y, 0deg))
    translateY(-10px);
  border-color: rgba(255, 184, 108, 0.38);
  box-shadow: 0 30px 72px rgba(0, 0, 0, 0.36);
}

.featured {
  background:
    linear-gradient(135deg, rgba(255, 122, 24, 0.12), transparent 36%),
    linear-gradient(225deg, rgba(93, 214, 255, 0.1), transparent 38%),
    rgba(10, 18, 32, 0.82);
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
  border: 1px solid rgba(168, 180, 200, 0.14);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.04);
  aspect-ratio: 16 / 9;
}

.preview-badge {
  position: absolute;
  top: 12px;
  left: 12px;
  z-index: 2;
  padding: 8px 11px;
  border: 1px solid rgba(255, 255, 255, 0.16);
  border-radius: 999px;
  background: rgba(5, 11, 24, 0.72);
  color: #f7fbff;
  font-size: 0.68rem;
  font-weight: 850;
  letter-spacing: 0.13em;
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
    linear-gradient(135deg, rgba(11, 23, 41, 0.95), rgba(7, 17, 31, 0.9));
}

.preview-placeholder span {
  color: var(--text);
  font-size: 1.35rem;
  font-weight: 850;
}

.preview-placeholder small {
  color: var(--muted);
  font-size: 0.88rem;
  letter-spacing: 0.08em;
  text-transform: uppercase;
}

.project-card:hover .preview-frame img {
  transform: scale(1.08);
  filter: saturate(1.12);
}

.preview-frame::after {
  content: "";
  position: absolute;
  inset: auto 0 0;
  height: 55%;
  background: linear-gradient(180deg, transparent, rgba(4, 8, 20, 0.44));
  pointer-events: none;
}

.preview-cta {
  position: absolute;
  right: 14px;
  bottom: 14px;
  z-index: 2;
  transform: translateY(10px);
  opacity: 0;
  transition: transform 0.25s ease, opacity 0.25s ease;
}

.preview-cta span {
  display: inline-flex;
  align-items: center;
  padding: 9px 12px;
  border-radius: 999px;
  background: rgba(255, 122, 24, 0.92);
  color: #07111f;
  font-size: 0.8rem;
  font-weight: 850;
  box-shadow: 0 16px 30px rgba(255, 122, 24, 0.28);
}

.project-card:hover .preview-cta {
  opacity: 1;
  transform: translateY(0);
}

.card-top {
  display: grid;
  gap: 10px;
}

.eyebrow {
  display: inline-block;
  margin-bottom: 10px;
  color: var(--accent-soft);
  font-size: 0.74rem;
  font-weight: 850;
  letter-spacing: 0.12em;
  text-transform: uppercase;
}

h3 {
  font-size: 1.55rem;
}

.category {
  color: var(--accent-cold);
  font-size: 0.9rem;
  font-weight: 850;
}

.description,
.highlights li {
  color: var(--muted);
  line-height: 1.7;
}

.highlights {
  display: grid;
  gap: 8px;
  list-style: none;
}

.highlights li {
  position: relative;
  padding-left: 18px;
}

.highlights li::before {
  content: "";
  position: absolute;
  left: 0;
  top: 10px;
  width: 7px;
  height: 7px;
  border-radius: 50%;
  background: var(--accent-green);
}

.techs {
  display: flex;
  flex-wrap: wrap;
  gap: 9px;
}

.techs span {
  padding: 8px 10px;
  border: 1px solid rgba(168, 180, 200, 0.14);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.04);
  color: #e5eef8;
  font-size: 0.86rem;
  font-weight: 800;
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
  gap: 10px;
  margin-top: auto;
}

.links a {
  padding: 11px 15px;
  border-radius: 12px;
  background: linear-gradient(135deg, var(--accent), #ffb15f);
  color: #081120;
  font-weight: 850;
  transition: transform 0.2s ease, box-shadow 0.25s ease;
}

.links a:hover {
  transform: translateY(-2px);
  box-shadow: 0 14px 28px rgba(255, 122, 24, 0.2);
}

.secondary-link {
  background: transparent !important;
  border: 1px solid rgba(168, 180, 200, 0.22);
  color: var(--text) !important;
}

@media (max-width: 640px) {
  .project-card {
    padding: 18px;
    border-radius: 20px;
  }
}
</style>
