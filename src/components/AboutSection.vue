<template>
  <section id="about" class="about">
    <p class="section-kicker">Sobre mí</p>
    <h2 class="section-title">Busco una primera experiencia profesional donde pueda aportar y acelerar mi crecimiento.</h2>

    <p class="section-subtitle">
      Me interesa trabajar en equipos donde pueda seguir aprendiendo, recibir feedback y participar en productos reales.
      Hoy mi foco está en construir soluciones completas, entender la lógica de negocio y mejorar tanto el frontend como el backend.
    </p>

    <div class="about-grid">
      <article class="glass-panel about-card intro-card">
        <span class="card-tag">Perfil</span>
        <h3>Base técnica con mentalidad práctica</h3>
        <p>
          Vengo formándome en desarrollo web con proyectos donde conecto interfaz, autenticación,
          base de datos, consumo de APIs y despliegue. No me interesa solo “que funcione”, sino entender por qué funciona.
        </p>
      </article>

      <article class="glass-panel about-card">
        <span class="card-tag">Fortalezas</span>
        <ul>
          <li>Aprendo rápido y me adapto bien a nuevas herramientas.</li>
          <li>Me siento cómodo armando proyectos full stack de punta a punta.</li>
          <li>Tengo interés real en soporte técnico, análisis y desarrollo.</li>
        </ul>
      </article>

      <article class="glass-panel metric-card">
        <strong>4+</strong>
        <p>proyectos publicados y deployados para mostrar trabajo real.</p>
      </article>

      <article class="glass-panel metric-card">
        <strong>Full stack</strong>
        <p>frontend, backend, JWT, MongoDB y despliegue en la nube.</p>
      </article>
    </div>
  </section>
</template>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: 1.15fr 1fr;
  gap: 22px;
}

.about-card,
.metric-card {
  border-radius: 26px;
  border: 1px solid var(--line);
}

.about-card {
  padding: 28px;
}

.intro-card {
  min-height: 100%;
}

.card-tag {
  display: inline-block;
  margin-bottom: 16px;
  padding: 8px 12px;
  border-radius: 999px;
  background: rgba(255, 122, 24, 0.12);
  color: var(--accent-soft);
  font-size: 0.78rem;
  font-weight: 800;
  letter-spacing: 0.1em;
  text-transform: uppercase;
}

h3 {
  margin-bottom: 14px;
  font-size: 1.5rem;
}

.about-card p,
.about-card li,
.metric-card p {
  color: var(--muted);
  line-height: 1.8;
}

ul {
  list-style: none;
  display: grid;
  gap: 12px;
}

li {
  position: relative;
  padding-left: 20px;
}

li::before {
  content: "";
  position: absolute;
  left: 0;
  top: 12px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--accent-cold);
}

.metric-card {
  padding: 24px;
  display: grid;
  align-content: center;
  min-height: 180px;
}

.metric-card strong {
  margin-bottom: 12px;
  font-size: clamp(1.8rem, 1.2rem + 2vw, 3rem);
  color: var(--accent-soft);
}

@media (max-width: 900px) {
  .about-grid {
    grid-template-columns: 1fr;
  }

  .metric-card {
    min-height: auto;
  }
}
</style>