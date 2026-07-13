<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <h1>{{ t('heroTitle') }}</h1>
        <p class="role">{{ t('heroRole') }}</p>
        <p class="subtitle">{{ t('heroSubtitle') }}</p>
        <p class="location">📍 {{ t('heroLocation') }}</p>
        <div class="hero-buttons">
          <a href="/Sedric_Kouam_Resume.pdf" download="Sedric_Kouam_Resume.pdf"><button class="btn btn-primary">{{ t('downloadResume') }}</button></a>
          <a href="#projects"><button class="btn btn-secondary">{{ t('viewMyWork') }}</button></a>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { onMounted, inject } from 'vue'
import { setMeta } from '../meta.js'

export default {
  name: 'Hero',
  setup() {
    const t = inject('t')
    const locale = inject('locale')
    
    onMounted(() => {
      const titles = {
        en: "Sedric Gerve Kouam | Full-Stack Developer & AI / Data Specialist",
        fr: "Sedric Gerve Kouam | Développeur Full-Stack & Spécialiste IA / Données"
      }
      const descriptions = {
        en: "Official portfolio of Sedric Gerve Kouam, full-stack web developer specialized in Data & Human-AI Interaction. Discover his projects, skills, experience, certifications and contact him directly.",
        fr: "Portfolio officiel de Sedric Gerve Kouam, développeur web full-stack spécialisé en Données & Interaction Humain-IA. Découvrez ses projets, compétences, expériences, certifications et contactez-le directement."
      }
      
      setMeta({
        title: titles[locale.value] || titles.en,
        description: descriptions[locale.value] || descriptions.en
      })
    })
    
    return { t }
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
  margin-bottom: 6px;
}

.role {
  font-size: 1.5rem;
  font-weight: 600;
  margin-bottom: 1.2rem;
  color: var(--white);
}

.subtitle {
  font-size: 1.15rem;
  max-width: 720px;
  margin: 0 auto 1.2rem;
  color: rgba(255, 255, 255, 0.9);
}

.location {
  font-size: 0.95rem;
  margin-bottom: 2rem;
  color: rgba(255, 255, 255, 0.85);
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
