<template>
  <section id="about" class="about">
    <h2 class="section-title">Sobre mí</h2>

    <p class="section-subtitle">
      Soy Lucas Rey, estudiante de Analista de Sistemas y desarrollador en formación.
      Me interesa crear aplicaciones reales, bien estructuradas y con una experiencia
      de usuario clara. Actualmente estoy fortaleciendo mis conocimientos en frontend,
      backend, bases de datos y despliegue en la nube.
    </p>

    <div class="about-grid">
      <article>
        <h3>Perfil</h3>
        <p>
          Busco mi primera oportunidad en tecnología, especialmente en roles trainee
          o junior relacionados con desarrollo web, soporte técnico o análisis de sistemas.
        </p>
      </article>

      <article>
        <h3>Enfoque</h3>
        <p>
          Me gusta aprender construyendo proyectos completos: frontend, backend,
          autenticación, base de datos, deploy y documentación.
        </p>
      </article>
    </div>
  </section>
</template>

<style scoped>
.about {
  background: #020617;
}

.about-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 22px;
}

article {
  background: #0f172a;
  border: 1px solid rgba(148, 163, 184, 0.15);
  padding: 24px;
  border-radius: 20px;
}

h3 {
  color: #38bdf8;
  margin-bottom: 12px;
}

p {
  color: #94a3b8;
  line-height: 1.7;
}

@media (max-width: 768px) {
  .about-grid {
    grid-template-columns: 1fr;
  }
}
</style>