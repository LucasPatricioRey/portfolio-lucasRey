<script setup>
const skills = [
  "HTML",
  "CSS",
  "JavaScript",
  "Vue.js",
  "Node.js",
  "Express",
  "MongoDB",
  "Git",
  "GitHub",
  "Netlify",
  "Render",
  "JWT"
];
</script>

<template>
  <section id="skills" class="skills">
    <h2 class="section-title">Skills</h2>

    <p class="section-subtitle">
      Tecnologías y herramientas que vengo usando en mis proyectos de portfolio.
    </p>

    <div class="skills-grid">
      <span v-for="skill in skills" :key="skill">
        {{ skill }}
      </span>
    </div>
  </section>
</template>

<style scoped>
.skills {
  background: #020617;
}

.skills-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 14px;
}

span {
  background: #0f172a;
  border: 1px solid rgba(56, 189, 248, 0.25);
  color: #e0f2fe;
  padding: 12px 16px;
  border-radius: 999px;
  font-weight: 700;
}
</style>