<template>
  <section class="hero">
    <div class="container">
      <div class="hero-content">
        <h1>{{ t('heroTitle') }}</h1>
        <p class="role">{{ t('heroRole') }}</p>
        <p class="subtitle">{{ t('heroSubtitle') }}</p>
        <p class="location">📍 {{ t('heroLocation') }}</p>
        <div class="hero-buttons">
          <a href="/Sedric_Kouam_Resume.pdf" download="Sedric_Kouam_Resume.pdf"><button class="btn btn-secondary">{{ t('downloadResume') }}</button></a>
          <a href="#projects"><button class="btn btn-primary">{{ t('viewMyWork') }}</button></a>
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
  background: var(--primary-color);
  position: relative;
  overflow: hidden;
  color: var(--white);
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 95vh;
  text-align: center;
}

.container {
  position: relative;
  z-index: 2;
}

.hero-content {
  animation: fadeInUp 0.9s ease-out;
}

.hero h1 {
  color: var(--white);
  margin-bottom: 12px;
  font-size: 4rem;
  font-weight: 800;
  letter-spacing: -1.5px;
  text-shadow: 0 2px 10px rgba(0, 0, 0, 0.2);
}

.role {
  font-size: 1.6rem;
  font-weight: 700;
  margin-bottom: 1.5rem;
  color: var(--accent-color);
}

.subtitle {
  font-size: 1.2rem;
  max-width: 800px;
  margin: 0 auto 1.5rem;
  color: rgba(255, 255, 255, 0.9);
  line-height: 1.8;
  font-weight: 400;
}

.location {
  font-size: 1rem;
  margin-bottom: 2.5rem;
  color: rgba(255, 255, 255, 0.8);
  font-weight: 500;
  letter-spacing: 0.5px;
}

.hero-buttons {
  display: flex;
  gap: 1.5rem;
  justify-content: center;
  flex-wrap: wrap;
  animation: fadeInUp 0.9s ease-out 0.2s both;
}

.btn {
  padding: 14px 32px;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.2);
}

.btn-primary {
  background-color: var(--accent-color);
  color: var(--white);
}

.btn-primary:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(249, 115, 22, 0.4);
  background-color: #EA580C;
}

.btn-secondary {
  background-color: transparent;
  color: var(--accent-color);
  border: 2.5px solid var(--accent-color);
}

.btn-secondary:hover {
  background-color: var(--accent-color);
  color: var(--white);
  transform: translateY(-4px);
  box-shadow: 0 10px 30px rgba(249, 115, 22, 0.3);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .hero {
    min-height: 70vh;
  }

  .hero h1 {
    font-size: 1.75rem;
    margin-bottom: 8px;
  }

  .role {
    font-size: 1rem;
    margin-bottom: 0.8rem;
  }

  .subtitle {
    font-size: 0.9rem;
    margin: 0 auto 1rem;
  }

  .location {
    font-size: 0.85rem;
    margin-bottom: 1.5rem;
  }

  .hero-buttons {
    gap: 0.8rem;
  }

  .btn {
    padding: 10px 18px;
    font-size: 0.85rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .hero {
    min-height: 80vh;
  }

  .hero h1 {
    font-size: 2.25rem;
  }

  .role {
    font-size: 1.3rem;
  }

  .subtitle {
    font-size: 1rem;
  }

  .hero-buttons {
    gap: 1rem;
  }

  .btn {
    padding: 11px 22px;
    font-size: 0.9rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .hero {
    min-height: 90vh;
  }

  .hero h1 {
    font-size: 3.2rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .hero {
    min-height: 95vh;
  }
}
</style>
