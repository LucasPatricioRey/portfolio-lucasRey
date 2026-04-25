<template>
  <section id="contact" class="contact">
    <h2 class="section-title">Contacto</h2>

    <p class="section-subtitle">
      Estoy buscando mi primera oportunidad en tecnología. Si querés contactarme,
      podés escribirme por email o revisar mis proyectos en GitHub.
    </p>

    <div class="contact-card">
      <a href="lucas1998z@ghotmail.com">lucas1998z@ghotmail.com</a>
      <a href="https://github.com/LucasPatricioRey" target="_blank">GitHub</a>
      <a href="https://www.linkedin.com/in/lucas-rey-685b93261/" target="_blank">LinkedIn</a>
    </div>
  </section>
</template>

<style scoped>
.contact {
  background:
    radial-gradient(circle at center, rgba(56, 189, 248, 0.12), transparent 34%),
    #020617;
}

.contact-card {
  background: #0f172a;
  border: 1px solid rgba(148, 163, 184, 0.18);
  border-radius: 22px;
  padding: 24px;
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
}

a {
  background: #2563eb;
  color: white;
  padding: 12px 16px;
  border-radius: 12px;
  font-weight: 800;
}

a:nth-child(2),
a:nth-child(3) {
  background: transparent;
  border: 1px solid #334155;
  color: #cbd5e1;
}
</style>