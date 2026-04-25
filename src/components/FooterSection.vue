<template>
  <footer>
    <p>© 2026 Lucas Rey. Portfolio desarrollado con Vue.js y una identidad visual más personal.</p>
  </footer>
</template>

<style scoped>
footer {
  width: min(1180px, calc(100% - 48px));
  margin: 0 auto 28px;
  padding: 24px 20px;
  border-top: 1px solid rgba(168, 180, 200, 0.14);
  color: var(--muted);
  text-align: center;
}

@media (max-width: 768px) {
  footer {
    width: min(100% - 28px, 1180px);
    margin-bottom: 20px;
  }
}
</style>