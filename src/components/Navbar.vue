<template>
  <header class="navbar">
    <a href="#home" class="logo">Lucas<span>Rey</span></a>

    <nav>
      <a href="#about">Sobre mí</a>
      <a href="#skills">Skills</a>
      <a href="#projects">Proyectos</a>
      <a href="#contact">Contacto</a>
    </nav>
  </header>
</template>

<style scoped>
.navbar {
  position: sticky;
  top: 0;
  z-index: 10;
  background: rgba(2, 6, 23, 0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(148, 163, 184, 0.16);
  padding: 18px 8%;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.logo {
  font-size: 22px;
  font-weight: 800;
}

.logo span {
  color: #38bdf8;
}

nav {
  display: flex;
  gap: 22px;
}

nav a {
  color: #cbd5e1;
  font-weight: 600;
}

nav a:hover {
  color: #38bdf8;
}

@media (max-width: 768px) {
  .navbar {
    flex-direction: column;
    gap: 14px;
  }

  nav {
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>