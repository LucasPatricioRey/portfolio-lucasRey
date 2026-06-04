<script setup>
const flowSteps = [
  {
    number: "01",
    title: "Idea comercial",
    text: "Defino el tipo de negocio, el objetivo de conversion y el recorrido que tiene que entender cualquier visitante."
  },
  {
    number: "02",
    title: "Interfaz con impacto",
    text: "Armo una pantalla principal fuerte, responsive, con visuales claros y llamados a la accion listos para vender."
  },
  {
    number: "03",
    title: "Flujo funcional",
    text: "Conecto interacciones: turnos, carrito, reservas, filtros, contacto por WhatsApp o paneles de gestion."
  },
  {
    number: "04",
    title: "Deploy y prueba",
    text: "Publico la demo, reviso mobile y dejo enlaces, repos y previews para que se pueda evaluar en minutos."
  }
];

const stackItems = ["Discovery", "UI", "UX", "Frontend", "API", "Deploy"];
</script>

<template>
  <section id="flow" class="flow-section">
    <div class="flow-header">
      <p class="section-kicker">Flujo</p>
      <h2 class="section-title">De una idea de negocio a una demo que se puede abrir, probar y mostrar.</h2>
      <p class="section-subtitle">
        El portfolio no solo lista proyectos: muestra un proceso. Cada demo tiene concepto,
        identidad visual, interaccion real y deploy publico.
      </p>
    </div>

    <div class="flow-board">
      <div class="flow-track" aria-hidden="true">
        <span></span>
      </div>

      <article
        v-for="(step, index) in flowSteps"
        :key="step.number"
        class="flow-step"
        :style="{ '--step-index': index }"
      >
        <span class="step-number">{{ step.number }}</span>
        <h3>{{ step.title }}</h3>
        <p>{{ step.text }}</p>
      </article>
    </div>

    <div class="flow-stack" aria-label="Capas del proceso">
      <span v-for="item in stackItems" :key="item">{{ item }}</span>
    </div>
  </section>
</template>

<style scoped>
.flow-section {
  width: min(1320px, calc(100% - 48px));
}

.flow-header {
  max-width: 900px;
}

.flow-board {
  position: relative;
  display: grid;
  grid-template-columns: repeat(4, minmax(0, 1fr));
  gap: 16px;
  padding: 28px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 28px;
  overflow: hidden;
  background:
    linear-gradient(135deg, rgba(77, 216, 255, 0.12), transparent 32%),
    linear-gradient(225deg, rgba(255, 107, 53, 0.13), transparent 34%),
    rgba(15, 11, 22, 0.78);
  box-shadow: 0 30px 92px rgba(0, 0, 0, 0.34);
}

.flow-board::before {
  content: "";
  position: absolute;
  inset: 0;
  background-image:
    linear-gradient(rgba(255, 255, 255, 0.045) 1px, transparent 1px),
    linear-gradient(90deg, rgba(255, 255, 255, 0.045) 1px, transparent 1px);
  background-size: 34px 34px;
  opacity: 0.35;
  pointer-events: none;
}

.flow-track {
  position: absolute;
  left: 42px;
  right: 42px;
  top: 82px;
  height: 3px;
  overflow: hidden;
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.12);
}

.flow-track span {
  display: block;
  width: 34%;
  height: 100%;
  border-radius: inherit;
  background: linear-gradient(90deg, transparent, var(--accent-cold), var(--accent-soft), transparent);
  animation: flowRunner 3.8s cubic-bezier(0.22, 1, 0.36, 1) infinite;
}

.flow-step {
  position: relative;
  z-index: 1;
  min-height: 260px;
  display: flex;
  flex-direction: column;
  gap: 14px;
  padding: 22px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 20px;
  background: rgba(255, 255, 255, 0.055);
  backdrop-filter: blur(14px);
  animation: stepFloat 5s ease-in-out infinite;
  animation-delay: calc(var(--step-index) * 180ms);
}

.step-number {
  width: 58px;
  height: 58px;
  display: grid;
  place-items: center;
  border: 1px solid rgba(255, 209, 102, 0.32);
  border-radius: 18px;
  background: rgba(255, 209, 102, 0.13);
  color: var(--accent-soft);
  font-weight: 950;
}

.flow-step h3 {
  font-size: clamp(1.22rem, 0.5vw + 1rem, 1.65rem);
}

.flow-step p {
  color: var(--muted);
  line-height: 1.7;
}

.flow-step::after {
  content: "";
  position: absolute;
  inset: auto 18px 18px;
  height: 3px;
  border-radius: 999px;
  background: linear-gradient(90deg, var(--accent), var(--accent-cold), var(--accent-green));
  transform: scaleX(0);
  transform-origin: left;
  animation: stepLoad 4.8s ease-in-out infinite;
  animation-delay: calc(var(--step-index) * 240ms);
}

.flow-stack {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
  margin-top: 18px;
}

.flow-stack span {
  padding: 10px 13px;
  border: 1px solid rgba(255, 255, 255, 0.14);
  border-radius: 999px;
  background: rgba(255, 255, 255, 0.06);
  color: #fff7e7;
  font-weight: 850;
}

@keyframes flowRunner {
  from {
    transform: translateX(-110%);
  }

  to {
    transform: translateX(310%);
  }
}

@keyframes stepFloat {
  0%,
  100% {
    transform: translateY(0);
  }

  50% {
    transform: translateY(-8px);
  }
}

@keyframes stepLoad {
  0%,
  35% {
    transform: scaleX(0);
    opacity: 0.45;
  }

  62% {
    transform: scaleX(1);
    opacity: 1;
  }

  100% {
    transform: scaleX(1);
    opacity: 0.25;
  }
}

@media (max-width: 1020px) {
  .flow-board {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }

  .flow-track {
    display: none;
  }
}

@media (max-width: 640px) {
  .flow-section {
    width: min(100% - 28px, 1320px);
  }

  .flow-board {
    grid-template-columns: 1fr;
    padding: 16px;
    border-radius: 22px;
  }

  .flow-step {
    min-height: auto;
    animation: none;
  }
}
</style>
