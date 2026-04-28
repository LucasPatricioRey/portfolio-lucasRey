<template>
  <section id="home" class="hero">
    <div class="hero-copy">
      <p class="eyebrow">Disponible para oportunidades trainee y junior</p>

      <h1>
        Desarrollo experiencias web con foco en <span>claridad, funcionalidad y crecimiento real</span>.
      </h1>

      <p class="intro">
        Soy Lucas Rey, estudiante de Analista de Sistemas. Me estoy especializando en desarrollo
        full stack con proyectos reales, autenticación, APIs, bases de datos y despliegues listos para producción.
      </p>

      <div class="hero-actions">
        <a href="#projects" class="btn btn-primary">Ver proyectos</a>
        <a href="#contact" class="btn btn-secondary">Hablemos</a>
        <a href="/cv-lucas-rey.pdf" class="btn btn-ghost" download>Descargar CV</a>
      </div>

      <ul class="hero-points glass-panel">
        <li>Frontend con Vue, HTML, CSS y JavaScript.</li>
        <li>Backend con Node.js, Express, JWT y MongoDB.</li>
        <li>Objetivo actual: sumar experiencia profesional y seguir creciendo rápido.</li>
      </ul>
    </div>

    <div class="hero-visual">
      <div class="photo-card glass-panel">
        <div class="orbit orbit-one"></div>
        <div class="orbit orbit-two"></div>

        <div class="photo-header">
          <span class="status-dot"></span>
          <p>Lucas Rey</p>
          <span class="status-label">Open to work</span>
        </div>

        <div class="photo-frame">
          <img src="/lucas-rey-photo.png" alt="Retrato de Lucas Rey" class="profile-photo" />
        </div>

        <div class="photo-footer">
          <div>
            <strong>Full Stack Junior</strong>
            <p>Desarrollo web, soporte técnico y análisis de sistemas.</p>
          </div>
          <img src="/lucas-rey-avatar.png" alt="Avatar ilustrado de Lucas Rey" class="avatar-badge" />
        </div>
      </div>

      <div class="hero-note glass-panel">
        <span>Stack principal</span>
        <p>Vue.js, Node.js, Express, MongoDB, Git y despliegue en Vercel/Render.</p>

        <div class="stack-marquee" aria-hidden="true">
          <span>Vue</span>
          <span>Node.js</span>
          <span>MongoDB</span>
          <span>JWT</span>
          <span>APIs</span>
          <span>Vercel</span>
          <span>Vue</span>
          <span>Node.js</span>
          <span>MongoDB</span>
          <span>JWT</span>
          <span>APIs</span>
          <span>Vercel</span>
        </div>
      </div>
    </div>
  </section>
</template>

<style scoped>
.hero {
  min-height: calc(100vh - 118px);
  display: grid;
  grid-template-columns: minmax(0, 1.2fr) minmax(320px, 0.95fr);
  align-items: center;
  gap: 48px;
  padding-top: 56px;
  position: relative;
  overflow: hidden;
}

.hero-copy {
  position: relative;
  z-index: 1;
}

.hero::before,
.hero::after {
  content: "";
  position: absolute;
  border-radius: 999px;
  filter: blur(24px);
  pointer-events: none;
}

.hero::before {
  width: 380px;
  height: 380px;
  top: 2%;
  right: 8%;
  background: radial-gradient(circle, rgba(93, 214, 255, 0.18), transparent 68%);
  animation: floatAura 9s ease-in-out infinite;
}

.hero::after {
  width: 340px;
  height: 340px;
  left: -2%;
  bottom: 8%;
  background: radial-gradient(circle, rgba(255, 122, 24, 0.2), transparent 68%);
  animation: floatAura 11s ease-in-out infinite reverse;
}

.eyebrow {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  margin-bottom: 22px;
  padding: 10px 14px;
  border-radius: 999px;
  background: rgba(93, 214, 255, 0.1);
  color: var(--accent-cold);
  font-weight: 800;
  box-shadow: 0 10px 30px rgba(93, 214, 255, 0.08);
}

.eyebrow::before {
  content: "";
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #35f08a;
  box-shadow: 0 0 18px rgba(53, 240, 138, 0.8);
  animation: statusBlink 2.8s ease-in-out infinite;
}

h1 {
  max-width: 12ch;
  font-size: clamp(3rem, 6vw, 5.4rem);
  line-height: 0.98;
  margin-bottom: 22px;
}

h1 span {
  color: var(--accent-soft);
  text-shadow: 0 0 26px rgba(255, 184, 108, 0.12);
}

.intro {
  max-width: 640px;
  color: var(--muted);
  line-height: 1.9;
  font-size: 1.08rem;
}

.hero-actions {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
  margin: 28px 0 30px;
}

.btn {
  padding: 14px 20px;
  border-radius: 14px;
  font-weight: 800;
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease, box-shadow 0.25s ease;
}

.hero-actions .btn:hover {
  transform: translateY(-4px) scale(1.02);
}

.btn-primary {
  background: linear-gradient(135deg, var(--accent), #ff9a3c);
  color: #081120;
  box-shadow: 0 18px 42px rgba(255, 122, 24, 0.22);
}

.btn-secondary {
  background: linear-gradient(135deg, #5dd6ff, #9be7ff);
  color: #07111f;
  box-shadow: 0 16px 36px rgba(93, 214, 255, 0.18);
}

.btn-ghost {
  border: 1px solid rgba(168, 180, 200, 0.25);
  color: var(--text);
}

.hero-points {
  list-style: none;
  display: grid;
  gap: 14px;
  padding: 22px;
  border-radius: 24px;
  box-shadow: 0 18px 46px rgba(0, 0, 0, 0.22);
}

.hero-points li {
  position: relative;
  padding-left: 20px;
  color: var(--muted);
  line-height: 1.7;
}

.hero-points li::before {
  content: "";
  position: absolute;
  left: 0;
  top: 11px;
  width: 8px;
  height: 8px;
  border-radius: 50%;
  background: var(--accent-soft);
}

.hero-visual {
  display: grid;
  gap: 18px;
}

.photo-card,
.hero-note {
  border-radius: 28px;
}

.photo-card {
  position: relative;
  padding: 20px;
  overflow: hidden;
  isolation: isolate;
  box-shadow: 0 30px 92px rgba(0, 0, 0, 0.42);
}

.photo-card::before {
  content: "";
  position: absolute;
  inset: -35% auto auto -15%;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(255, 122, 24, 0.14), transparent 68%);
  pointer-events: none;
}

.orbit {
  position: absolute;
  border-radius: 999px;
  border: 1px solid rgba(255, 255, 255, 0.09);
  pointer-events: none;
  z-index: 0;
}

.orbit-one {
  inset: 10% -8% auto auto;
  width: 170px;
  height: 170px;
  border-right-color: rgba(93, 214, 255, 0.34);
  border-top-color: rgba(93, 214, 255, 0.18);
  animation: orbitSpin 12s linear infinite;
}

.orbit-two {
  inset: auto auto 14% -5%;
  width: 128px;
  height: 128px;
  border-left-color: rgba(255, 122, 24, 0.3);
  border-bottom-color: rgba(255, 184, 108, 0.2);
  animation: orbitSpin 16s linear infinite reverse;
}

.photo-header,
.photo-footer {
  display: flex;
  align-items: center;
}

.photo-header {
  gap: 10px;
  margin-bottom: 18px;
  color: var(--muted);
}

.photo-header p {
  font-weight: 700;
}

.status-dot {
  width: 10px;
  height: 10px;
  border-radius: 50%;
  background: #35f08a;
  box-shadow: 0 0 16px rgba(53, 240, 138, 0.9);
  animation: statusBlink 2.8s ease-in-out infinite;
}

.status-label {
  margin-left: auto;
  padding: 8px 10px;
  border-radius: 999px;
  background: rgba(255, 122, 24, 0.16);
  color: var(--accent-soft);
  font-size: 0.78rem;
  font-weight: 800;
  animation: labelPulse 5s ease-in-out infinite;
}

.photo-frame {
  position: relative;
  overflow: hidden;
  border-radius: 26px;
  border: 1px solid rgba(168, 180, 200, 0.14);
  background: linear-gradient(180deg, rgba(255, 255, 255, 0.05), rgba(255, 255, 255, 0.01));
}

.photo-frame::before {
  content: "";
  position: absolute;
  inset: 0 auto 0 -60%;
  width: 38%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.1), transparent);
  transform: skewX(-18deg);
  animation: sweepGlow 7.2s ease-in-out infinite;
  pointer-events: none;
  z-index: 1;
}

.photo-frame::after {
  content: "";
  position: absolute;
  inset: auto 0 0;
  height: 36%;
  background: linear-gradient(180deg, transparent, rgba(7, 17, 31, 0.85));
}

.photo-frame img,
.photo-frame::before,
.photo-frame::after,
.photo-header,
.photo-footer {
  position: relative;
  z-index: 1;
}

.profile-photo {
  width: 100%;
  aspect-ratio: 4 / 5;
  object-fit: cover;
  object-position: center 18%;
  transform: scale(1.01);
  transition: transform 0.45s ease;
}

.photo-card:hover .profile-photo {
  transform: scale(1.045);
}

.photo-footer {
  gap: 16px;
  margin-top: 16px;
}

.photo-footer strong {
  display: block;
  margin-bottom: 6px;
  font-size: 1.05rem;
}

.photo-footer p {
  color: var(--muted);
  line-height: 1.7;
}

.avatar-badge {
  width: 82px;
  height: 82px;
  object-fit: cover;
  border-radius: 24px;
  border: 1px solid rgba(168, 180, 200, 0.18);
  background: rgba(4, 8, 20, 0.85);
  padding: 6px;
  transition: transform 0.25s ease;
}

.photo-card:hover .avatar-badge {
  transform: translateY(-6px) rotate(-4deg) scale(1.04);
}

.hero-note {
  position: relative;
  padding: 20px 22px;
  overflow: hidden;
  box-shadow: 0 24px 64px rgba(0, 0, 0, 0.3);
}

.hero-note::after {
  content: "";
  position: absolute;
  inset: auto -20% -80% auto;
  width: 180px;
  height: 180px;
  border-radius: 50%;
  background: radial-gradient(circle, rgba(93, 214, 255, 0.12), transparent 70%);
  pointer-events: none;
}

.hero-note span {
  display: block;
  margin-bottom: 10px;
  color: var(--accent-cold);
  font-size: 0.85rem;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.16em;
}

.hero-note p {
  color: var(--muted);
  line-height: 1.8;
}

.stack-marquee {
  display: flex;
  gap: 10px;
  width: 100%;
  max-width: 100%;
  margin-top: 18px;
  flex-wrap: wrap;
}

.stack-marquee span {
  padding: 8px 12px;
  border-radius: 999px;
  border: 1px solid rgba(168, 180, 200, 0.16);
  background: rgba(255, 255, 255, 0.05);
  color: #edf4fb;
  font-size: 0.84rem;
  font-weight: 700;
  white-space: nowrap;
}

@keyframes statusBlink {
  0%,
  100% {
    transform: scale(1);
    opacity: 1;
  }

  45% {
    transform: scale(0.88);
    opacity: 0.72;
  }

  55% {
    transform: scale(1.08);
    opacity: 1;
  }
}

@keyframes sweepGlow {
  0%,
  100% {
    transform: translateX(0) skewX(-18deg);
    opacity: 0;
  }

  18%,
  28% {
    opacity: 1;
  }

  42% {
    transform: translateX(320%) skewX(-18deg);
    opacity: 0;
  }
}

@keyframes labelPulse {
  0%,
  100% {
    box-shadow: 0 0 0 rgba(255, 122, 24, 0);
  }

  50% {
    box-shadow: 0 0 0 8px rgba(255, 122, 24, 0.06);
  }
}

@keyframes floatAura {
  0%,
  100% {
    transform: translate3d(0, 0, 0) scale(1);
    opacity: 0.8;
  }

  50% {
    transform: translate3d(14px, -18px, 0) scale(1.08);
    opacity: 1;
  }
}

@keyframes orbitSpin {
  from {
    transform: rotate(0deg);
  }

  to {
    transform: rotate(360deg);
  }
}

@keyframes marqueeDrift {
  0% {
    transform: translateX(0);
  }

  100% {
    transform: translateX(-50%);
  }
}

@media (max-width: 980px) {
  .hero {
    grid-template-columns: 1fr;
    min-height: auto;
  }

  h1 {
    max-width: 100%;
  }
}

@media (max-width: 640px) {
  .hero {
    gap: 30px;
    padding-top: 30px;
  }

  .stack-marquee {
    gap: 8px;
  }

  .photo-card {
    padding: 14px;
  }

  .photo-footer {
    align-items: flex-start;
  }

  .avatar-badge {
    width: 68px;
    height: 68px;
  }
}
</style>
