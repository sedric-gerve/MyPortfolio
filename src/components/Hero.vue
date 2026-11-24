<template>
  <section class="hero">
    <div class="grid-overlay" aria-hidden="true"></div>
    <div class="container">
      <div class="hero-grid">
        <div class="hero-content">
          <p class="role">{{ t('heroRole') }}</p>

          <div class="build-line">
            <span class="build-label">{{ t('servicesLabel') }}</span>
            <span class="leader" aria-hidden="true"></span>
            <Transition name="swap" mode="out-in">
              <span :key="currentService" class="build-tag">{{ currentService }}</span>
            </Transition>
          </div>

          <p class="subtitle">{{ t('heroSubtitle') }}</p>

          <div class="meta-tags">
            <span class="tag"><span class="status-dot" aria-hidden="true"></span>{{ t('heroLocation') }}</span>
            <span class="tag">{{ t('heroAvailability') }}</span>
          </div>

          <div class="hero-buttons">
            <a href="/Sedric_Kouam_Resume_2026-11.pdf" download="Sedric_Kouam_Resume.pdf"><button class="btn btn-secondary">{{ t('downloadResume') }}</button></a>
            <a href="#projects"><button class="btn btn-primary">{{ t('viewMyWork') }}</button></a>
          </div>
        </div>

        <div class="hero-visual" aria-hidden="true">
          <div class="visual-frame">
            <img
              v-for="(image, i) in visuals"
              :key="image"
              :src="image"
              alt=""
              class="visual-image"
              :class="{ active: i === visualIndex }"
            />
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { onMounted, onUnmounted, inject, ref, computed } from 'vue'
import { setMeta } from '../meta.js'

export default {
  name: 'Hero',
  setup() {
    const t = inject('t')
    const locale = inject('locale')

    const serviceKeys = ['service1', 'service2', 'service3', 'service4']
    const serviceIndex = ref(0)
    const currentService = computed(() => t(serviceKeys[serviceIndex.value]))
    let serviceTimer = null

    const visuals = ['/hero-visual-1.jpg', '/hero-visual-2.jpg', '/hero-visual-3.webp']
    const visualIndex = ref(0)
    let visualTimer = null

    onMounted(() => {
      const titles = {
        en: "Sedric Gerve Kouam | Full-Stack Developer & AI / Data Specialist",
        fr: "Sedric Gerve Kouam | Développeur Full-Stack & Spécialiste IA / Données"
      }
      const descriptions = {
        en: "Official portfolio of Sedric Gerve Kouam, full-stack web developer specialized in Data & Human-AI Interaction. Discover his services, projects, skills and contact him directly.",
        fr: "Portfolio officiel de Sedric Gerve Kouam, développeur web full-stack spécialisé en Données & Interaction Humain-IA. Découvrez ses services, projets, compétences et contactez-le directement."
      }

      setMeta({
        title: titles[locale.value] || titles.en,
        description: descriptions[locale.value] || descriptions.en
      })

      serviceTimer = setInterval(() => {
        serviceIndex.value = (serviceIndex.value + 1) % serviceKeys.length
      }, 2200)

      visualTimer = setInterval(() => {
        visualIndex.value = (visualIndex.value + 1) % visuals.length
      }, 3200)
    })

    onUnmounted(() => {
      if (serviceTimer) clearInterval(serviceTimer)
      if (visualTimer) clearInterval(visualTimer)
    })

    return { t, currentService, visuals, visualIndex }
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
  min-height: 95vh;
  text-align: left;
}

.grid-overlay {
  position: absolute;
  inset: 0;
  pointer-events: none;
  background-image:
    linear-gradient(var(--line-on-ink) 1px, transparent 1px),
    linear-gradient(90deg, var(--line-on-ink) 1px, transparent 1px);
  background-size: 56px 56px;
  mask-image: radial-gradient(ellipse 90% 70% at 20% 30%, black 40%, transparent 85%);
  -webkit-mask-image: radial-gradient(ellipse 90% 70% at 20% 30%, black 40%, transparent 85%);
}

.container {
  position: relative;
  z-index: 2;
}

.hero-grid {
  display: grid;
  grid-template-columns: minmax(0, 1.15fr) minmax(0, 0.85fr);
  align-items: center;
  gap: 3rem;
  width: 100%;
}

.hero-content {
  max-width: 560px;
}

.hero-visual {
  position: relative;
}

.visual-frame {
  position: relative;
  aspect-ratio: 4 / 5;
  border: 1px solid var(--line-on-ink);
  border-radius: 8px;
  overflow: hidden;
  background: rgba(255, 255, 255, 0.03);
}

.visual-frame::before,
.visual-frame::after {
  content: '';
  position: absolute;
  width: 18px;
  height: 18px;
  border: 1.5px solid var(--accent-color);
  z-index: 2;
}

.visual-frame::before {
  top: -9px;
  left: -9px;
  border-right: none;
  border-bottom: none;
}

.visual-frame::after {
  bottom: -9px;
  right: -9px;
  border-left: none;
  border-top: none;
}

.visual-image {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  object-fit: cover;
  opacity: 0;
  transition: opacity 1.2s ease;
}

.visual-image.active {
  opacity: 1;
}

.role {
  font-family: var(--font-display);
  font-size: 1.05rem;
  font-weight: 500;
  letter-spacing: 0.02em;
  margin-bottom: 0.5rem;
  color: var(--accent-color);
}

.build-line {
  display: flex;
  align-items: center;
  gap: 0.6rem;
  margin-bottom: 1.8rem;
  font-size: 1.1rem;
  min-height: 2.4rem;
}

.build-label {
  font-weight: 500;
  color: rgba(255, 255, 255, 0.75);
}

.leader {
  width: 28px;
  height: 1px;
  background: var(--accent-color);
  flex-shrink: 0;
}

.build-tag {
  display: inline-block;
  font-family: var(--font-display);
  font-weight: 600;
  color: var(--white);
  border: 1px solid var(--accent-color);
  border-radius: 3px;
  padding: 0.3rem 0.85rem;
  position: relative;
}

.build-tag::before,
.build-tag::after {
  content: '';
  position: absolute;
  width: 5px;
  height: 5px;
  border: 1px solid var(--accent-color);
}

.build-tag::before {
  top: -4px;
  left: -4px;
  border-right: none;
  border-bottom: none;
}

.build-tag::after {
  bottom: -4px;
  right: -4px;
  border-left: none;
  border-top: none;
}

.swap-enter-active,
.swap-leave-active {
  transition: opacity 0.35s ease, transform 0.35s ease;
}

.swap-enter-from {
  opacity: 0;
  transform: translateY(4px);
}

.swap-leave-to {
  opacity: 0;
  transform: translateY(-4px);
}

.subtitle {
  font-size: 1.35rem;
  max-width: 640px;
  margin: 0 0 1.8rem;
  color: rgba(255, 255, 255, 0.82);
  line-height: 1.65;
  font-weight: 400;
}

.meta-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-bottom: 2.4rem;
}

.tag {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  font-size: 0.85rem;
  font-weight: 500;
  color: rgba(255, 255, 255, 0.85);
  border: 1px solid var(--line-on-ink);
  border-radius: 3px;
  padding: 0.35rem 0.7rem;
}

.status-dot {
  width: 6px;
  height: 6px;
  border-radius: 50%;
  background: var(--accent-color);
  flex-shrink: 0;
}

.hero-buttons {
  display: flex;
  gap: 1.2rem;
  flex-wrap: wrap;
}

.btn {
  padding: 14px 30px;
  border-radius: 4px;
  font-size: 1rem;
  font-weight: 600;
  transition: all 0.25s ease;
}

.btn-primary {
  background-color: var(--accent-color);
  color: var(--white);
}

.btn-primary:hover {
  background-color: #EA580C;
}

.btn-secondary {
  background-color: transparent;
  color: var(--white);
  border: 1px solid rgba(255, 255, 255, 0.4);
}

.btn-secondary:hover {
  border-color: var(--white);
  background-color: rgba(255, 255, 255, 0.06);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .hero {
    min-height: 70vh;
  }

  .hero-grid {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .hero-content {
    max-width: 100%;
  }

  .hero-visual {
    max-width: 260px;
  }

  .role {
    font-size: 0.9rem;
  }

  .build-line {
    font-size: 0.9rem;
    margin-bottom: 1.2rem;
  }

  .subtitle {
    font-size: 1.05rem;
    margin-bottom: 1.2rem;
  }

  .meta-tags {
    margin-bottom: 1.6rem;
  }

  .hero-buttons {
    gap: 0.7rem;
  }

  .btn {
    padding: 11px 20px;
    font-size: 0.85rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .hero {
    min-height: 80vh;
  }

  .hero-grid {
    grid-template-columns: 1fr;
    gap: 2.4rem;
  }

  .hero-visual {
    max-width: 320px;
  }

  .subtitle {
    font-size: 1.2rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .hero {
    min-height: 90vh;
  }

  .hero-grid {
    gap: 2rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .hero {
    min-height: 95vh;
  }
}
</style>
