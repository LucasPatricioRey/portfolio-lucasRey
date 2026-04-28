<script setup>
import { skillGroups } from "../data/skills";

const techIcons = {
  html: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#E44D26" d="M3 2h18l-1.64 18.2L12 22l-7.36-1.8z"/><path fill="#F16529" d="M12 20.46l5.95-1.47L19.35 3H12z"/><path fill="#EBEBEB" d="M12 10.2H8.98l-.2-2.23H12V5.8H6.42l.05.58.53 5.98H12zm0 5.63-.01.01-2.5-.68-.16-1.84H7.08l.31 3.49 4.6 1.27h.01z"/><path fill="#FFF" d="M11.99 10.2v2.17h2.81l-.26 2.79-2.55.68v2.26l4.61-1.28.03-.37.52-5.88.06-.57zM11.99 5.8v2.17h5.39l.04-.48.09-1 .05-.58z"/>'
  },
  css: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#264DE4" d="M3 2h18l-1.64 18.2L12 22l-7.36-1.8z"/><path fill="#2965F1" d="M12 20.46l5.95-1.47L19.35 3H12z"/><path fill="#EBEBEB" d="M12 10.08H8.95l-.21-2.3H12V5.6H6.35l.06.6.56 6.06H12zm0 5.47-.01.01-2.52-.67-.16-1.78H7.09l.31 3.41 4.59 1.28h.01z"/><path fill="#FFF" d="M17.1 10.08l.06-.6.31-3.88H12v2.18h3.25l-.21 2.3H12v2.18h2.85l-.27 2.9-2.58.69v2.26l4.6-1.27.03-.37z"/>'
  },
  javascript: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#F7DF1E" d="M2 2h20v20H2z"/><path fill="#111827" d="M15.18 17.47c.4.66.93 1.15 1.86 1.15.78 0 1.28-.39 1.28-.93 0-.65-.52-.88-1.38-1.26l-.47-.2c-1.36-.58-2.26-1.31-2.26-2.84 0-1.41 1.08-2.49 2.77-2.49 1.2 0 2.06.42 2.68 1.51l-1.47.94c-.32-.58-.67-.81-1.21-.81s-.89.35-.89.81c0 .57.35.81 1.17 1.17l.47.2c1.6.68 2.5 1.38 2.5 2.95 0 1.69-1.33 2.61-3.12 2.61-1.75 0-2.88-.83-3.43-1.92zm-6.64.16c.3.53.57.97 1.22.97.62 0 1.02-.24 1.02-1.2v-6.5h1.89v6.53c0 1.98-1.16 2.89-2.86 2.89-1.53 0-2.42-.79-2.87-1.74z"/>'
  },
  vue: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#41B883" d="M2 4h4.27L12 13.47 17.73 4H22l-10 17z"/><path fill="#35495E" d="M6.27 4 12 13.47 17.73 4h-3.97L12 7.03 10.24 4z"/>'
  },
  node: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#539E43" d="M11.99 1.34 4.52 5.67a1.06 1.06 0 0 0-.53.92v8.67c0 .38.2.73.53.92L12 20.5c.33.19.74.19 1.06 0l7.47-4.32c.33-.19.53-.54.53-.92V6.59c0-.38-.2-.73-.53-.92l-7.47-4.33a1.06 1.06 0 0 0-1.07 0"/><path fill="#FFF" d="M12.42 6.1c-2.7 0-4.4 1.17-4.4 3.04 0 1.62.96 2.48 3 3l.93.24c1.01.26 1.44.53 1.44 1.07 0 .62-.6.99-1.6.99-1.26 0-1.95-.43-2.64-1.35l-1.3.76c.9 1.42 2.08 2.03 3.96 2.03 2.45 0 4-1.2 4-3.1 0-1.67-.98-2.41-3.08-2.95l-.93-.24c-1.01-.25-1.36-.46-1.36-.99 0-.5.45-.87 1.32-.87.96 0 1.52.33 2.06 1.08l1.33-.77c-.78-1.27-1.92-1.94-3.73-1.94"/>'
  },
  express: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#E8EEF9" d="M4.4 17.8V6.2h11.2v1.9H6.63v2.86h7.5v1.87h-7.5v3.08h9.06v1.89zm12.12-8.06 2.27-3.54h2.5l-3.46 5.2 3.6 6.4h-2.56l-2.42-4.37-2.43 4.36H11.5l3.64-6.35-3.45-5.25h2.54z"/>'
  },
  jwt: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#D63AFF" d="M12 2.5 8.75 5.75l1.46 1.46L12 5.43l1.79 1.78 1.46-1.46zm0 16.07-1.79-1.78-1.46 1.46L12 21.5l3.25-3.25-1.46-1.46z"/><path fill="#FB015B" d="m5.75 8.75-3.25 3.25 3.25 3.25 1.46-1.46L5.43 12l1.78-1.79zm12.5 0 1.78 1.79-1.78 1.79 1.46 1.46L22.96 12l-3.25-3.25z"/><path fill="#00F2E6" d="M15.25 8.75 12 12l3.25 3.25L16.7 13.8 14.91 12l1.79-1.79zm-6.5 0L7.3 10.2 9.09 12 7.3 13.79l1.45 1.46L12 12z"/>'
  },
  mongodb: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#13AA52" d="M12.2 2c-.77 1.89-1.3 4.45-1.11 6.87.11 1.52.56 3.03 1.54 4.36.77-.57 1.32-1.32 1.73-2.22.63-1.38.79-2.93.65-4.44-.17-1.76-.73-3.45-1.4-4.57-.13-.22-.28-.22-.41 0"/><path fill="#A6A385" d="M12 13.24c-.11-.08-.2-.16-.29-.25-.96-1.04-1.58-2.31-1.86-3.7-.16 2.16.34 4.68 2.15 6.61V22h.39v-6.1c1.52-1.7 2.3-3.84 2.22-6.16-.25 1.25-.84 2.43-1.8 3.36-.24.24-.51.45-.81.64"/>'
  },
  git: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#F05133" d="M23.56 10.87 13.13.44a1.5 1.5 0 0 0-2.12 0L8.84 2.61l2.75 2.75a1.78 1.78 0 0 1 2.26 2.27l2.65 2.65a1.78 1.78 0 1 1-1.07 1.02l-2.47-2.47v6.5a1.78 1.78 0 1 1-1.45-.03V8.74a1.78 1.78 0 0 1-.97-2.33L9.8 3.67.44 13.03a1.5 1.5 0 0 0 0 2.12l10.43 10.43a1.5 1.5 0 0 0 2.12 0l10.57-10.57a1.5 1.5 0 0 0 0-2.14"/>'
  },
  github: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#F8FAFC" d="M12 2C6.48 2 2 6.59 2 12.25c0 4.53 2.87 8.37 6.84 9.73.5.1.68-.22.68-.49 0-.24-.01-1.03-.01-1.87-2.78.62-3.37-1.22-3.37-1.22-.46-1.2-1.11-1.52-1.11-1.52-.91-.64.07-.62.07-.62 1 .07 1.53 1.05 1.53 1.05.9 1.56 2.35 1.11 2.92.85.09-.67.35-1.12.63-1.38-2.22-.26-4.56-1.14-4.56-5.08 0-1.12.39-2.03 1.03-2.75-.1-.26-.45-1.31.1-2.74 0 0 .84-.28 2.75 1.05A9.3 9.3 0 0 1 12 7.1c.85 0 1.7.12 2.5.35 1.9-1.33 2.74-1.05 2.74-1.05.56 1.43.21 2.48.1 2.74.64.72 1.03 1.63 1.03 2.75 0 3.95-2.34 4.81-4.57 5.06.36.32.68.96.68 1.94 0 1.4-.01 2.54-.01 2.88 0 .27.18.59.69.49A10.26 10.26 0 0 0 22 12.25C22 6.59 17.52 2 12 2"/>'
  },
  netlify: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#32E6E2" d="M6.63 4.15 9.5 7.02 6.63 9.89 3.76 7.02zm10.74 0 2.87 2.87-2.87 2.87-2.87-2.87zM6.63 14.11l2.87 2.87-2.87 2.87-2.87-2.87zm7.33-9.24h4.06v4.06h-4.06zm-7.98 7.98h4.06v4.06H5.98zm7.98 0h4.06v4.06h-4.06zm-2.94-2.94h4.06v4.06h-4.06z"/>'
  },
  render: {
    viewBox: "0 0 24 24",
    content:
      '<path fill="#8B5CF6" d="M5 4.5h7.53c3.13 0 5.17 1.96 5.17 4.9 0 2.52-1.53 4.25-3.9 4.67l4.2 5.43h-3.63l-3.83-5.1H8.03v5.1H5zm3.03 2.55v4.81h4.03c1.59 0 2.57-.92 2.57-2.42 0-1.48-.98-2.39-2.57-2.39z"/>'
  }
};
</script>

<template>
  <section id="skills" class="skills">
    <p class="section-kicker">Stack</p>
    <h2 class="section-title">Tecnologias con las que ya construyo proyectos completos.</h2>

    <p class="section-subtitle">
      Este stack refleja lo que hoy puedo llevar a la practica: interfaces, logica de servidor,
      autenticacion, base de datos y despliegue para dejar proyectos funcionando de verdad.
    </p>

    <div class="skills-grid">
      <article v-for="group in skillGroups" :key="group.title" class="glass-panel skill-card">
        <h3>{{ group.title }}</h3>
        <p>{{ group.description }}</p>

        <div class="skill-items">
          <span v-for="item in group.items" :key="item.label" class="skill-pill">
            <svg
              class="skill-icon"
              :viewBox="techIcons[item.icon].viewBox"
              aria-hidden="true"
              v-html="techIcons[item.icon].content"
            />
            {{ item.label }}
          </span>
        </div>
      </article>
    </div>
  </section>
</template>

<style scoped>
.skills-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 20px;
}

.skill-card {
  padding: 28px;
  border-radius: 26px;
}

.skill-card h3 {
  margin-bottom: 12px;
  font-size: 1.4rem;
}

.skill-card p {
  min-height: 86px;
  margin-bottom: 20px;
  color: var(--muted);
  line-height: 1.8;
}

.skill-items {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

.skill-pill {
  display: inline-flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
  border-radius: 999px;
  background: rgba(93, 214, 255, 0.08);
  border: 1px solid rgba(93, 214, 255, 0.16);
  color: #e7f9ff;
  font-weight: 700;
  transition: transform 0.2s ease, border-color 0.2s ease, background 0.2s ease;
}

.skill-card:hover .skill-pill {
  border-color: rgba(93, 214, 255, 0.24);
  background: rgba(93, 214, 255, 0.12);
}

.skill-pill:hover {
  transform: translateY(-2px);
}

.skill-icon {
  width: 18px;
  height: 18px;
  flex: 0 0 18px;
}

@media (max-width: 920px) {
  .skills-grid {
    grid-template-columns: 1fr;
  }

  .skill-card p {
    min-height: auto;
  }
}
</style>
