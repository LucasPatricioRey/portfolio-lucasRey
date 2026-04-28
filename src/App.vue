<script setup>
import { onBeforeUnmount, onMounted } from "vue";
import Navbar from "./components/Navbar.vue";
import HeroSection from "./components/HeroSection.vue";
import AboutSection from "./components/AboutSection.vue";
import SkillsSection from "./components/SkillsSection.vue";
import ProjectsSection from "./components/ProjectsSection.vue";
import ContactSection from "./components/ContactSection.vue";
import FooterSection from "./components/FooterSection.vue";

let revealObserver;
let pointerTargets = [];

const handlePointerMove = (event) => {
  const element = event.currentTarget;
  const bounds = element.getBoundingClientRect();
  const offsetX = (event.clientX - bounds.left) / bounds.width;
  const offsetY = (event.clientY - bounds.top) / bounds.height;
  const intensity = Number(element.dataset.tiltIntensity || 1);
  const rotateY = (offsetX - 0.5) * 12 * intensity;
  const rotateX = (0.5 - offsetY) * 10 * intensity;

  element.style.setProperty("--tilt-x", `${rotateX.toFixed(2)}deg`);
  element.style.setProperty("--tilt-y", `${rotateY.toFixed(2)}deg`);
  element.style.setProperty("--glow-x", `${(offsetX * 100).toFixed(2)}%`);
  element.style.setProperty("--glow-y", `${(offsetY * 100).toFixed(2)}%`);
};

const resetPointer = (event) => {
  const element = event.currentTarget;
  element.style.setProperty("--tilt-x", "0deg");
  element.style.setProperty("--tilt-y", "0deg");
  element.style.setProperty("--glow-x", "50%");
  element.style.setProperty("--glow-y", "50%");
};

onMounted(() => {
  const targets = [
    ...document.querySelectorAll("main > section"),
    ...document.querySelectorAll(".hero-copy > *"),
    ...document.querySelectorAll(".hero-visual > *"),
    ...document.querySelectorAll(".hero-points li"),
    ...document.querySelectorAll(".project-card"),
    ...document.querySelectorAll(".skill-card"),
    ...document.querySelectorAll(".about-card"),
    ...document.querySelectorAll(".metric-card"),
    ...document.querySelectorAll(".contact-card")
  ];

  targets.forEach((element, index) => {
    element.classList.add("motion-reveal");
    element.style.setProperty("--motion-delay", `${Math.min(index % 6, 5) * 70}ms`);
  });

  revealObserver = new IntersectionObserver(
    (entries) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          entry.target.classList.add("is-visible");
          revealObserver.unobserve(entry.target);
        }
      });
    },
    {
      threshold: 0.14,
      rootMargin: "0px 0px -8% 0px"
    }
  );

  targets.forEach((element) => revealObserver.observe(element));

  pointerTargets = [
    ...document.querySelectorAll(".project-card"),
    ...document.querySelectorAll(".photo-card"),
    ...document.querySelectorAll(".hero-note"),
    ...document.querySelectorAll(".skill-card"),
    ...document.querySelectorAll(".about-card")
  ];

  pointerTargets.forEach((element) => {
    element.classList.add("interactive-tilt");
    if (element.classList.contains("project-card")) {
      element.dataset.tiltIntensity = "1.2";
    } else if (element.classList.contains("photo-card")) {
      element.dataset.tiltIntensity = "1.1";
    } else {
      element.dataset.tiltIntensity = "0.9";
    }
    element.style.setProperty("--tilt-x", "0deg");
    element.style.setProperty("--tilt-y", "0deg");
    element.style.setProperty("--glow-x", "50%");
    element.style.setProperty("--glow-y", "50%");
    element.addEventListener("pointermove", handlePointerMove);
    element.addEventListener("pointerleave", resetPointer);
  });
});

onBeforeUnmount(() => {
  revealObserver?.disconnect();
  pointerTargets.forEach((element) => {
    element.removeEventListener("pointermove", handlePointerMove);
    element.removeEventListener("pointerleave", resetPointer);
  });
});
</script>

<template>
  <div class="app-shell">
    <Navbar />
    <main>
      <HeroSection />
      <AboutSection />
      <SkillsSection />
      <ProjectsSection />
      <ContactSection />
    </main>
    <FooterSection />
  </div>
</template>
