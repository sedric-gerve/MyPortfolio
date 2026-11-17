<template>
  <section id="experience" class="experience">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('experienceTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <div class="timeline">
        <div v-for="job in jobs" :key="job.id" class="timeline-item">
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <p class="date">{{ t(job.date) }}</p>
            <h3>{{ t(job.title) }}</h3>
            <p class="company">{{ t(job.company) }}</p>
            <p class="description">{{ t(job.description) }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Experience',
  setup() {
    const t = inject('t')
    return {
      t,
      jobs: [
        {
          id: 1,
          title: 'job1Title',
          company: 'job1Company',
          date: 'job1Date',
          description: 'job1Desc'
        },
        {
          id: 2,
          title: 'job2Title',
          company: 'job2Company',
          date: 'job2Date',
          description: 'job2Desc'
        },
        {
          id: 3,
          title: 'job3Title',
          company: 'job3Company',
          date: 'job3Date',
          description: 'job3Desc'
        }
      ]
    }
  }
}
</script>

<style scoped>
.experience {
  background: var(--primary-color);
  position: relative;
}

.experience::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.timeline {
  position: relative;
  max-width: 720px;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 5px;
  top: 6px;
  width: 1px;
  height: 100%;
  background: var(--line-on-ink);
}

.timeline-item {
  position: relative;
  padding-left: 2.5rem;
  margin-bottom: 2.5rem;
}

.timeline-item:last-child {
  margin-bottom: 0;
}

.timeline-marker {
  position: absolute;
  left: 0;
  top: 6px;
  width: 11px;
  height: 11px;
  background: var(--primary-color);
  border: 2px solid var(--accent-color);
}

.timeline-content {
  background: var(--paper);
  border: 1px solid var(--line-on-paper);
  border-radius: 4px;
  padding: 1.6rem 1.8rem;
  transition: border-color 0.2s ease;
}

.timeline-content:hover {
  border-color: var(--accent-color);
}

.date {
  color: var(--secondary-color);
  font-size: 0.82rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.timeline-content h3 {
  font-family: var(--font-display);
  color: var(--ink-on-paper);
  margin-bottom: 0.3rem;
  font-size: 1.2rem;
}

.company {
  color: var(--text-light);
  font-weight: 500;
  margin-bottom: 0.9rem;
  font-size: 0.95rem;
}

.description {
  color: var(--text-light);
  line-height: 1.65;
  font-size: 0.93rem;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .timeline-item {
    padding-left: 1.6rem;
    margin-bottom: 1.6rem;
  }

  .timeline-content {
    padding: 1.1rem 1.2rem;
  }

  .timeline-content h3 {
    font-size: 1.05rem;
  }

  .company {
    font-size: 0.88rem;
  }

  .description {
    font-size: 0.88rem;
  }
}
</style>
