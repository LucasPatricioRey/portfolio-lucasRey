<template>
  <section id="contact" class="contact">
    <p class="section-kicker">Contacto</p>
    <h2 class="section-title">Si te interesa mi perfil, me encantaría conversar.</h2>

    <p class="section-subtitle">
      Estoy buscando mi primera oportunidad en tecnología para aportar, aprender rápido y sumar experiencia.
      Si querés ver más de mi trabajo o hablar sobre una posición trainee o junior, te dejo mis canales directos.
    </p>

    <div class="contact-layout">
      <article class="glass-panel contact-card main-card">
        <span class="contact-label">Disponible</span>
        <h3>Lucas Rey</h3>
        <p>Desarrollador full stack junior con interés en desarrollo web, soporte técnico y análisis de sistemas.</p>
        <div class="cta-row">
          <a href="mailto:lucas1998z@hotmail.com" class="primary-link">Enviar email</a>
          <a href="/cv-lucas-rey.pdf" download class="secondary-link">Descargar CV</a>
        </div>
      </article>

      <div class="links-grid">
        <a href="https://github.com/LucasPatricioRey" target="_blank" rel="noopener noreferrer" class="glass-panel social-card">
          <span>GitHub</span>
          <strong>Ver repositorios</strong>
        </a>

        <a href="https://www.linkedin.com/in/lucas-rey-685b93261/" target="_blank" rel="noopener noreferrer" class="glass-panel social-card">
          <span>LinkedIn</span>
          <strong>Conectar profesionalmente</strong>
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.contact-layout {
  display: grid;
  grid-template-columns: 1.2fr 0.9fr;
  gap: 22px;
}

.contact-card,
.social-card {
  border-radius: 28px;
  border: 1px solid var(--line);
}

.contact-card {
  padding: 30px;
}

.contact-label {
  display: inline-flex;
  margin-bottom: 16px;
  padding: 8px 12px;
  border-radius: 999px;
  background: rgba(93, 214, 255, 0.1);
  color: var(--accent-cold);
  font-weight: 800;
}

.contact-card h3 {
  margin-bottom: 12px;
  font-size: 1.9rem;
}

.contact-card p {
  max-width: 560px;
  color: var(--muted);
  line-height: 1.8;
}

.cta-row {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  margin-top: 24px;
}

.cta-row a,
.social-card {
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.cta-row a:hover,
.social-card:hover {
  transform: translateY(-2px);
}

.primary-link,
.secondary-link {
  padding: 13px 18px;
  border-radius: 12px;
  font-weight: 800;
}

.primary-link {
  background: linear-gradient(135deg, var(--accent), #ff9a3c);
  color: #081120;
}

.secondary-link {
  border: 1px solid rgba(168, 180, 200, 0.24);
}

.links-grid {
  display: grid;
  gap: 22px;
}

.social-card {
  min-height: 156px;
  padding: 24px;
  display: grid;
  align-content: end;
}

.social-card span {
  margin-bottom: 12px;
  color: var(--accent-soft);
  font-size: 0.82rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.14em;
}

.social-card strong {
  font-size: 1.3rem;
  line-height: 1.4;
}

@media (max-width: 900px) {
  .contact-layout {
    grid-template-columns: 1fr;
  }
}
</style>