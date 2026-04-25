<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <p class="tag">Portfolio Personal</p>

      <h1>
        Hola, soy <span>Lucas Rey</span>
      </h1>

      <h2>Desarrollador Full Stack Junior</h2>

      <p class="description">
        Estudiante de Analista de Sistemas enfocado en construir aplicaciones web
        modernas, funcionales y conectadas a bases de datos reales.
      </p>

      <div class="actions">
        <a href="#projects" class="btn primary">Ver proyectos</a>
        <a href="/cv-lucas-rey.pdf" class="btn secondary" download>Descargar CV</a>
        <a href="#contact" class="btn ghost">Contactarme</a>
      </div>
    </div>

    <div class="hero-card">
      <p class="card-label">Disponible</p>
      <h3>Oportunidades trainee / junior</h3>
      <p>Vue.js · Node.js · Express · MongoDB</p>
      <span>Frontend, backend, soporte técnico y análisis de sistemas.</span>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: calc(100vh - 74px);
  display: grid;
  grid-template-columns: 1.4fr 0.9fr;
  align-items: center;
  gap: 40px;
  background:
    radial-gradient(circle at top right, rgba(56, 189, 248, 0.18), transparent 34%),
    radial-gradient(circle at bottom left, rgba(37, 99, 235, 0.18), transparent 36%);
}

.tag {
  display: inline-block;
  color: #38bdf8;
  font-weight: 700;
  margin-bottom: 16px;
}

h1 {
  font-size: clamp(42px, 7vw, 58px);
  line-height: 1.1;
  margin-bottom: 12px;
}

h1 span {
  color: #38bdf8;
}

h2 {
  color: #cbd5e1;
  font-size: clamp(22px, 3vw, 28px);
  margin-bottom: 20px;
}

.description {
  max-width: 650px;
  color: #94a3b8;
  line-height: 1.8;
  font-size: 18px;
}

.actions {
  margin-top: 30px;
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
}

.btn {
  padding: 13px 18px;
  border-radius: 12px;
  font-weight: 800;
  transition: 0.2s ease;
}

.btn:hover {
  transform: translateY(-2px);
}

.primary {
  background: #2563eb;
  color: white;
}

.secondary {
  background: #38bdf8;
  color: #020617;
}

.ghost {
  border: 1px solid #334155;
  color: #cbd5e1;
}

.hero-card {
  background: rgba(15, 23, 42, 0.86);
  border: 1px solid rgba(148, 163, 184, 0.18);
  padding: 28px;
  border-radius: 24px;
  box-shadow: 0 24px 70px rgba(0, 0, 0, 0.35);
}

.card-label {
  display: inline-block;
  color: #38bdf8;
  font-weight: 800;
  margin-bottom: 12px;
}

.hero-card h3 {
  margin-bottom: 10px;
  font-size: 24px;
}

.hero-card p:not(.card-label) {
  color: #38bdf8;
  font-weight: 800;
  margin-bottom: 18px;
}

.hero-card span {
  color: #94a3b8;
  line-height: 1.6;
}

@media (max-width: 900px) {
  .hero {
    grid-template-columns: 1fr;
  }
}
</style>
