<template>
  <header class="navbar">
    <a href="#home" class="logo">Lucas<span>Rey</span></a>

    <nav>
      <a href="#demos">Demos</a>
      <a href="#flow">Flujo</a>
      <a href="#about">Sobre mi</a>
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
  width: min(1320px, calc(100% - 48px));
  margin: 16px auto 0;
  padding: 12px 16px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  border: 1px solid rgba(255, 255, 255, 0.13);
  border-radius: 18px;
  background: rgba(10, 7, 14, 0.72);
  box-shadow: 0 18px 50px rgba(0, 0, 0, 0.28);
  backdrop-filter: blur(18px);
}

.logo {
  font-size: 1.25rem;
  font-weight: 900;
}

.logo span {
  color: var(--accent-cold);
}

nav {
  display: flex;
  flex-wrap: wrap;
  gap: 7px;
}

nav a {
  padding: 9px 12px;
  border-radius: 12px;
  color: var(--muted);
  font-size: 0.94rem;
  font-weight: 800;
  transition: color 0.2s ease, background 0.2s ease, transform 0.2s ease;
}

nav a:hover {
  color: var(--text);
  background: rgba(255, 255, 255, 0.075);
  transform: translateY(-1px);
}

@media (max-width: 768px) {
  .navbar {
    top: 8px;
    width: min(100% - 20px, 1320px);
    padding: 10px 12px;
    gap: 10px;
    flex-direction: column;
    align-items: flex-start;
    border-radius: 16px;
  }

  .logo {
    flex: 0 0 auto;
    font-size: 1.02rem;
  }

  nav {
    width: 100%;
    flex: 1 1 auto;
    flex-wrap: nowrap;
    justify-content: flex-start;
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
    width: min(100% - 16px, 1320px);
    gap: 8px;
  }

  .logo {
    font-size: 0.96rem;
  }

  nav {
    justify-content: flex-start;
    gap: 2px;
  }

  nav a {
    padding: 7px 6px;
    font-size: 0.72rem;
  }
}
</style>
