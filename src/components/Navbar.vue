<template>
  <header class="navbar">
    <a href="#home" class="logo">Lucas<span>Rey</span></a>

    <nav>
      <a href="#about">Sobre mí</a>
      <a href="#skills">Stack</a>
      <a href="#projects">Proyectos</a>
      <a href="#contact">Contacto</a>
    </nav>
  </header>
</template>

<style scoped>
.navbar {
  position: sticky;
  top: 16px;
  z-index: 20;
  width: min(1180px, calc(100% - 48px));
  margin: 16px auto 0;
  padding: 16px 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border-radius: 22px;
  background: rgba(5, 12, 23, 0.7);
  border: 1px solid rgba(168, 180, 200, 0.16);
  backdrop-filter: blur(18px);
}

.logo {
  font-size: 1.25rem;
  font-weight: 800;
}

.logo span {
  color: var(--accent-soft);
}

nav {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}

nav a {
  padding: 10px 14px;
  border-radius: 999px;
  color: var(--muted);
  font-size: 0.95rem;
  font-weight: 700;
  transition: 0.2s ease;
}

nav a:hover {
  color: var(--text);
  background: rgba(255, 255, 255, 0.06);
}

@media (max-width: 768px) {
  .navbar {
    top: 8px;
    width: min(100% - 20px, 1180px);
    padding: 10px 12px;
    gap: 10px;
    border-radius: 18px;
  }

  .logo {
    flex: 0 0 auto;
    font-size: 1.02rem;
  }

  nav {
    flex: 1 1 auto;
    flex-wrap: nowrap;
    justify-content: flex-end;
    gap: 4px;
    overflow-x: auto;
    scrollbar-width: none;
  }

  nav::-webkit-scrollbar {
    display: none;
  }

  nav a {
    flex: 0 0 auto;
    padding: 8px 9px;
    font-size: 0.8rem;
    white-space: nowrap;
  }
}

@media (max-width: 420px) {
  .navbar {
    width: min(100% - 16px, 1180px);
    gap: 8px;
  }

  .logo {
    font-size: 0.96rem;
  }

  nav {
    justify-content: flex-end;
    gap: 2px;
  }

  nav a {
    padding: 7px 6px;
    font-size: 0.72rem;
  }
}
</style>
