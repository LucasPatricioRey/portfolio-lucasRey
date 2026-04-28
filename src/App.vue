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
});

onBeforeUnmount(() => {
  revealObserver?.disconnect();
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
