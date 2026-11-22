<template>
  <section id="services" class="services">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('servicesTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <p class="services-intro">{{ t('servicesIntro') }}</p>

      <div class="services-grid">
        <article v-for="service in services" :key="service.id" class="service-card">
          <span class="service-icon">{{ service.icon }}</span>
          <h3>{{ t(service.name) }}</h3>
          <p>{{ t(service.description) }}</p>
          <div class="service-tags">
            <span v-for="tag in service.tags" :key="tag" class="tag">{{ tag }}</span>
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
    return {
      t,
      services: [
        {
          id: 1,
          name: 'svcWebName',
          description: 'svcWebDesc',
          icon: '💻',
          tags: ['Laravel', 'Vue.js', 'TALL Stack']
        },
        {
          id: 2,
          name: 'svcAgentsName',
          description: 'svcAgentsDesc',
          icon: '🤖',
          tags: ['n8n', 'Claude', 'Automation']
        },
        {
          id: 3,
          name: 'svcRagName',
          description: 'svcRagDesc',
          icon: '🔍',
          tags: ['PostgreSQL + pgvector', 'Voyage AI', 'Claude']
        },
        {
          id: 4,
          name: 'svcSeoName',
          description: 'svcSeoDesc',
          icon: '📈',
          tags: ['Core Web Vitals', 'Structured Data', 'Performance']
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

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.service-card {
  background: var(--paper);
  border: 1px solid var(--line-on-paper);
  border-radius: 4px;
  padding: 2rem;
  transition: border-color 0.2s ease;
}

.service-card:hover {
  border-color: var(--accent-color);
}

.service-icon {
  font-size: 2rem;
  margin-bottom: 1.2rem;
  display: inline-block;
}

.service-card h3 {
  font-family: var(--font-display);
  color: var(--ink-on-paper);
  margin-bottom: 0.6rem;
  font-size: 1.15rem;
}

.service-card p {
  color: var(--text-light);
  line-height: 1.6;
  font-size: 0.92rem;
  margin-bottom: 1.4rem;
}

.service-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  border-top: 1px solid var(--line-on-paper);
  padding-top: 1.2rem;
}

.tag {
  color: var(--secondary-color);
  padding: 0.25rem 0.6rem;
  border-radius: 2px;
  font-size: 0.74rem;
  font-weight: 500;
  border: 1px solid var(--line-on-paper);
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
