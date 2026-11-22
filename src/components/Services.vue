<template>
  <section id="services" class="services">
    <div class="container">
      <span class="eyebrow">{{ t('servicesEyebrow') }}</span>
      <div class="section-head">
        <h2>{{ t('servicesTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <p class="services-intro">{{ t('servicesIntro') }}</p>

      <div class="services-grid">
        <article
          v-for="(service, index) in services"
          :key="service.id"
          class="service-card"
          :class="{ featured: service.featured }"
        >
          <span class="service-number">{{ ref(index) }}</span>
          <h3>{{ t(service.name) }}</h3>
          <p>{{ t(service.description) }}</p>
          <span class="service-category">{{ t(service.category) }}</span>
        </article>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Services',
  setup() {
    const t = inject('t')
    const ref = (index) => String(index + 1).padStart(2, '0')
    return {
      t,
      ref,
      services: [
        {
          id: 1,
          name: 'svcWebName',
          category: 'svcWebCategory',
          description: 'svcWebDesc'
        },
        {
          id: 2,
          name: 'svcAgentsName',
          category: 'svcAgentsCategory',
          description: 'svcAgentsDesc',
          featured: true
        },
        {
          id: 3,
          name: 'svcRagName',
          category: 'svcRagCategory',
          description: 'svcRagDesc'
        },
        {
          id: 4,
          name: 'svcSeoName',
          category: 'svcSeoCategory',
          description: 'svcSeoDesc'
        },
        {
          id: 5,
          name: 'svcDeployName',
          category: 'svcDeployCategory',
          description: 'svcDeployDesc'
        }
      ]
    }
  }
}
</script>

<style scoped>
.services {
  background: var(--primary-color);
  position: relative;
}

.services::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.eyebrow {
  display: block;
  color: var(--accent-color);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.services-intro {
  color: var(--text-on-dark-muted);
  font-size: 1.05rem;
  max-width: 560px;
  margin-top: -2.5rem;
  margin-bottom: 3.5rem;
}

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.service-card {
  background: var(--paper);
  border: 1px solid var(--line-on-paper);
  border-radius: 8px;
  padding: 2rem;
  transition: border-color 0.2s ease;
}

.service-card:hover {
  border-color: var(--accent-color);
}

.service-card.featured {
  border: 1.5px solid var(--accent-color);
}

.service-number {
  display: block;
  font-family: var(--font-display);
  color: var(--accent-color);
  font-size: 0.85rem;
  font-weight: 700;
  margin-bottom: 0.9rem;
}

.service-card h3 {
  font-family: var(--font-display);
  color: var(--ink-on-paper);
  margin-bottom: 0.6rem;
  font-size: 1.2rem;
}

.service-card p {
  color: var(--text-light);
  line-height: 1.6;
  font-size: 0.92rem;
  margin-bottom: 1.4rem;
}

.service-category {
  display: block;
  color: var(--text-lighter);
  font-size: 0.72rem;
  font-weight: 600;
  letter-spacing: 0.08em;
  text-transform: uppercase;
  border-top: 1px solid var(--line-on-paper);
  padding-top: 1rem;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .services-intro {
    margin-top: 0;
    margin-bottom: 2rem;
  }

  .services-grid {
    grid-template-columns: 1fr;
    gap: 1.2rem;
  }

  .service-card {
    padding: 1.4rem;
  }

  .service-card h3 {
    font-size: 1.05rem;
  }

  .service-card p {
    font-size: 0.88rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .services-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
