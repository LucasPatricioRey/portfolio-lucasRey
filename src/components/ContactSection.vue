<script setup>
import { ref } from "vue";

const email = "lucas1998z@hotmail.com";
const copied = ref(false);

const copyEmail = async () => {
  try {
    await navigator.clipboard.writeText(email);
    copied.value = true;
    window.setTimeout(() => {
      copied.value = false;
    }, 1800);
  } catch {
    copied.value = false;
  }
};
</script>

<template>
  <section id="contact" class="contact">
    <p class="section-kicker">Contacto</p>
    <h2 class="section-title">Si te interesa mi perfil para una posicion trainee o junior, conversemos.</h2>

    <p class="section-subtitle">
      Estoy buscando una primera oportunidad en tecnologia para seguir creciendo sobre proyectos reales.
      Te dejo canales directos para revisar mi trabajo, escribirme o descargar el CV.
    </p>

    <div class="contact-layout">
      <article class="glass-panel contact-card main-card">
        <span class="contact-label">Disponible</span>
        <h3>Lucas Rey</h3>
        <p>Desarrollador frontend junior con base full stack, foco en productos web y experiencia construyendo proyectos deployados.</p>

        <div class="email-box">
          <span>Email</span>
          <strong>{{ email }}</strong>
        </div>

        <div class="cta-row">
          <a
            :href="`mailto:${email}?subject=Contacto%20desde%20tu%20portfolio&body=Hola%20Lucas%2C%20vi%20tu%20portfolio%20y%20queria%20contactarte.`"
            class="primary-link"
          >
            Enviar email
          </a>
          <button type="button" class="secondary-link" @click="copyEmail">
            {{ copied ? "Email copiado" : "Copiar email" }}
          </button>
          <a href="/cv-lucas-rey.pdf" download class="secondary-link">Descargar CV</a>
        </div>
      </article>

      <div class="links-grid">
        <a href="https://www.linkedin.com/in/lucas-rey-685b93261/" target="_blank" rel="noopener noreferrer" class="glass-panel social-card linkedin-card">
          <span>LinkedIn</span>
          <strong>Conectar y ver mi perfil profesional</strong>
        </a>

        <a href="https://github.com/LucasPatricioRey" target="_blank" rel="noopener noreferrer" class="glass-panel social-card">
          <span>GitHub</span>
          <strong>Ver proyectos, codigo y repositorios</strong>
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
  border: 1px solid var(--line);
  border-radius: 24px;
}

.contact-card {
  padding: 30px;
}

.contact-label {
  display: inline-flex;
  margin-bottom: 16px;
  padding: 8px 12px;
  border-radius: 999px;
  background: rgba(54, 211, 153, 0.1);
  color: var(--accent-green);
  font-weight: 850;
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

.email-box {
  margin-top: 22px;
  padding: 16px;
  border: 1px solid rgba(168, 180, 200, 0.16);
  border-radius: 16px;
  background: rgba(255, 255, 255, 0.045);
}

.email-box span {
  display: block;
  margin-bottom: 6px;
  color: var(--accent-cold);
  font-size: 0.78rem;
  font-weight: 850;
  letter-spacing: 0;
  text-transform: uppercase;
}

.email-box strong {
  word-break: break-word;
}

.cta-row {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-top: 22px;
}

.cta-row a,
.cta-row button,
.social-card {
  transition: transform 0.2s ease, border-color 0.2s ease;
}

.cta-row a:hover,
.cta-row button:hover,
.social-card:hover {
  transform: translateY(-2px);
}

.primary-link,
.secondary-link {
  min-height: 46px;
  padding: 13px 18px;
  border-radius: 12px;
  font: inherit;
  font-weight: 850;
  cursor: pointer;
}

.primary-link {
  background: linear-gradient(135deg, var(--accent), #ffb15f);
  color: #081120;
}

.secondary-link {
  border: 1px solid rgba(168, 180, 200, 0.24);
  background: transparent;
  color: var(--text);
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

.linkedin-card {
  background:
    linear-gradient(135deg, rgba(93, 214, 255, 0.12), transparent 42%),
    rgba(10, 18, 32, 0.82);
}

.social-card span {
  margin-bottom: 12px;
  color: var(--accent-soft);
  font-size: 0.82rem;
  font-weight: 850;
  text-transform: uppercase;
  letter-spacing: 0;
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

@media (max-width: 520px) {
  .contact-card {
    padding: 22px;
  }

  .cta-row {
    display: grid;
  }
}
</style>
