<template>
  <section id="services" class="services">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('servicesTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <p class="services-intro">{{ t('servicesIntro') }}</p>

      <div class="services-list">
        <article
          v-for="(service, index) in services"
          :key="service.id"
          class="service-row"
          :class="{ featured: service.featured }"
        >
          <div class="service-head">
            <span class="service-number">{{ ref(index) }}</span>
            <h3>{{ t(service.name) }}</h3>
            <p class="service-category">{{ t(service.category) }}</p>
          </div>
          <div class="service-body">
            <p class="service-description">{{ t(service.description) }}</p>
            <span class="includes-label">{{ t('includesLabel') }}</span>
            <div class="includes-grid">
              <span v-for="item in service.includes" :key="item" class="includes-item">
                <span class="bullet" aria-hidden="true"></span>{{ t(item) }}
              </span>
            </div>
          </div>
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
          description: 'svcWebDesc',
          includes: ['svcWebInc1', 'svcWebInc2', 'svcWebInc3', 'svcWebInc4']
        },
        {
          id: 2,
          name: 'svcAgentsName',
          category: 'svcAgentsCategory',
          description: 'svcAgentsDesc',
          includes: ['svcAgentsInc1', 'svcAgentsInc2', 'svcAgentsInc3', 'svcAgentsInc4'],
          featured: true
        },
        {
          id: 3,
          name: 'svcRagName',
          category: 'svcRagCategory',
          description: 'svcRagDesc',
          includes: ['svcRagInc1', 'svcRagInc2', 'svcRagInc3', 'svcRagInc4']
        },
        {
          id: 4,
          name: 'svcSeoName',
          category: 'svcSeoCategory',
          description: 'svcSeoDesc',
          includes: ['svcSeoInc1', 'svcSeoInc2', 'svcSeoInc3', 'svcSeoInc4']
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

.services-intro {
  color: var(--text-on-dark-muted);
  font-size: 1.05rem;
  max-width: 560px;
  margin-top: -2.5rem;
  margin-bottom: 3.5rem;
}

.services-list {
  border-top: 1px solid var(--line-on-ink);
}

.service-row {
  display: grid;
  grid-template-columns: 1fr 1.4fr;
  gap: 3rem;
  padding: 3rem 0;
  border-bottom: 1px solid var(--line-on-ink);
}

.service-row.featured .service-number {
  color: var(--accent-color);
}

.service-number {
  display: block;
  font-family: var(--font-display);
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-on-dark-muted);
  margin-bottom: 0.8rem;
}

.service-head h3 {
  color: var(--white);
  font-size: 1.5rem;
  margin-bottom: 0.4rem;
}

.service-category {
  color: var(--text-on-dark-muted);
  font-size: 0.9rem;
}

.service-description {
  color: var(--text-on-dark-muted);
  font-size: 1rem;
  line-height: 1.7;
  margin-bottom: 1.5rem;
  max-width: 480px;
}

.includes-label {
  display: block;
  color: var(--accent-color);
  font-size: 0.82rem;
  font-weight: 600;
  margin-bottom: 1rem;
}

.includes-grid {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 0.8rem 1.5rem;
  max-width: 480px;
}

.includes-item {
  display: flex;
  align-items: baseline;
  gap: 0.6rem;
  color: var(--white);
  font-size: 0.92rem;
}

.bullet {
  width: 5px;
  height: 5px;
  background: var(--accent-color);
  flex-shrink: 0;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .services-intro {
    margin-top: 0;
    margin-bottom: 2rem;
  }

  .service-row {
    grid-template-columns: 1fr;
    gap: 1.2rem;
    padding: 2rem 0;
  }

  .service-head h3 {
    font-size: 1.25rem;
  }

  .includes-grid {
    grid-template-columns: 1fr;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .service-row {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}
</style>
