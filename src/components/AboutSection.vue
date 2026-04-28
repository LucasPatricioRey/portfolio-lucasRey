<template>
  <section id="about" class="about">
    <p class="section-kicker">Sobre mi</p>
    <h2 class="section-title">Busco una primera experiencia profesional para aportar desde el primer dia y seguir creciendo con desafios reales.</h2>

    <p class="section-subtitle">
      Hoy me estoy enfocando en construir aplicaciones completas, entender la logica de negocio y
      trabajar con una mentalidad practica. Me interesa sumar a un equipo donde pueda aportar con
      ejecucion, seguir aprendiendo y crecer rapido sobre proyectos reales.
    </p>

    <div class="about-grid">
      <article class="glass-panel about-card intro-card">
        <span class="card-tag">Perfil</span>
        <h3>Frontend junior con base full stack</h3>
        <p>
          Vengo trabajando con proyectos donde conecto interfaz, autenticacion, APIs,
          base de datos y despliegue. Me interesa construir productos claros, funcionales
          y bien resueltos, no solo llegar a una demo que funcione.
        </p>
      </article>

      <article class="glass-panel about-card">
        <span class="card-tag">Fortalezas</span>
        <ul>
          <li>Puedo construir aplicaciones de punta a punta con frontend y backend.</li>
          <li>Me adapto rapido y aprendo bien cuando trabajo sobre problemas concretos.</li>
          <li>Me interesa combinar desarrollo web, soporte tecnico y analisis de sistemas.</li>
        </ul>
      </article>

      <article class="glass-panel metric-card">
        <strong>6+</strong>
        <p>proyectos publicados para mostrar trabajo real y evolucion tecnica.</p>
      </article>

      <article class="glass-panel metric-card">
        <strong>Deploy real</strong>
        <p>apps con autenticacion, APIs, MongoDB y despliegue en la nube.</p>
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
