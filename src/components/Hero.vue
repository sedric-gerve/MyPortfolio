<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <h1>Sedrick Kouam – Développeur Web Full Stack</h1>
        <p class="subtitle">Full Stack Developer | TALL Stack Specialist | 6 Years of Experience</p>
        <div class="hero-buttons">
          <button class="btn btn-primary">Download Resume</button>
          <button class="btn btn-secondary">View My Work</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { onMounted } from 'vue'
import { setMeta } from '../meta.js'

export default {
  name: 'Hero',
  setup() {
    onMounted(() => {
      setMeta({
        title: "Sedrick Kouam | Portfolio Développeur Web Full Stack",
        description: "Portfolio officiel de Sedrick Kouam, développeur web full stack. Découvrez ses projets, compétences, expériences et contactez-le directement."
      })
    })
  }
}
</script>

<style scoped>
.hero {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
  display: flex;
  align-items: center;
  min-height: 90vh;
  text-align: center;
}

.hero-content {
  animation: fadeInUp 0.8s ease;
}

.hero h1 {
  color: var(--white);
  margin-bottom: 10px;
}

.subtitle {
  font-size: 1.3rem;
  margin-bottom: 2rem;
  color: rgba(255, 255, 255, 0.9);
}

.hero-buttons {
  display: flex;
  gap: 1rem;
  justify-content: center;
  flex-wrap: wrap;
}

.btn {
  padding: 12px 30px;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 600;
  transition: all 0.3s;
}

.btn-primary {
  background-color: var(--white);
  color: var(--primary-color);
}

.btn-primary:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0, 0, 0, 0.2);
}

.btn-secondary {
  background-color: transparent;
  color: var(--white);
  border: 2px solid var(--white);
}

.btn-secondary:hover {
  background-color: var(--white);
  color: var(--primary-color);
  transform: translateY(-3px);
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>
