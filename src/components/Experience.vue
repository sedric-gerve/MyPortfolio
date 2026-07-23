<template>
  <section id="experience" class="experience">
    <div class="container">
      <h2>{{ t('experienceTitle') }}</h2>
      <div class="timeline">
        <div v-for="job in jobs" :key="job.id" class="timeline-item">
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <h3>{{ t(job.title) }}</h3>
            <p class="company">{{ t(job.company) }}</p>
            <p class="date">{{ t(job.date) }}</p>
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
  background: linear-gradient(180deg, var(--white) 0%, var(--bg-light) 100%);
  position: relative;
}

.experience::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.experience h2 {
  text-align: center;
  margin-bottom: 4rem;
  animation: fadeInUp 0.7s ease-out;
}

.timeline {
  position: relative;
  padding: 3rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 3px;
  height: 100%;
  background: linear-gradient(180deg, var(--secondary-color), var(--accent-color));
  box-shadow: 0 0 20px rgba(37, 99, 235, 0.3);
}

.timeline-item {
  margin-bottom: 3rem;
  position: relative;
  opacity: 0;
  animation: fadeInUp 0.7s ease-out forwards;
}

.timeline-item:nth-child(1) { animation-delay: 0.1s; }
.timeline-item:nth-child(2) { animation-delay: 0.2s; }
.timeline-item:nth-child(3) { animation-delay: 0.3s; }

.timeline-item:nth-child(odd) .timeline-content {
  margin-left: 0;
  margin-right: 52%;
  text-align: right;
}

.timeline-item:nth-child(even) .timeline-content {
  margin-left: 52%;
  margin-right: 0;
  text-align: left;
}

.timeline-marker {
  position: absolute;
  left: 50%;
  top: 0;
  transform: translateX(-50%);
  width: 20px;
  height: 20px;
  background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
  border: 4px solid var(--white);
  border-radius: 50%;
  z-index: 1;
  box-shadow: 0 0 20px rgba(37, 99, 235, 0.4);
  transition: all 0.3s ease;
}

.timeline-item:hover .timeline-marker {
  width: 28px;
  height: 28px;
  transform: translateX(-50%);
}

.timeline-content {
  background: var(--white);
  padding: 2rem;
  border-radius: 12px;
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.08);
  border: 1px solid var(--bg-light);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.timeline-content::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 300px;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(37, 99, 235, 0.1), transparent);
  transition: left 0.5s ease;
}

.timeline-item:hover .timeline-content {
  transform: translateY(-4px);
  box-shadow: 0 12px 35px rgba(37, 99, 235, 0.15);
  border-color: var(--secondary-color);
}

.timeline-item:hover .timeline-content::before {
  left: 100%;
}

.timeline-content h3 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
  font-size: 1.3rem;
}

.company {
  color: var(--secondary-color);
  font-weight: 700;
  margin-bottom: 0.5rem;
  font-size: 1rem;
}

.date {
  color: var(--text-lighter);
  font-size: 0.85rem;
  font-weight: 500;
  margin-bottom: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
}

.description {
  color: var(--text-light);
  line-height: 1.7;
  font-size: 0.95rem;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .timeline::before {
    display: none;
  }

  .timeline-item {
    padding-left: 2rem;
    margin-bottom: 1.5rem;
  }

  .timeline-content {
    padding: 1.2rem;
    text-align: left;
  }

  .timeline-marker {
    left: 0;
    width: 16px;
    height: 16px;
  }

  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    margin: 0;
    text-align: left;
  }

  .timeline-content h3 {
    font-size: 1.05rem;
    margin-bottom: 0.4rem;
  }

  .company {
    font-size: 0.9rem;
  }

  .date {
    font-size: 0.75rem;
  }

  .description {
    font-size: 0.9rem;
  }

  .experience h2 {
    margin-bottom: 2rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .timeline::before {
    display: none;
  }

  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    margin-left: 0;
    margin-right: 0;
    text-align: left;
  }

  .timeline-marker {
    left: 0;
    top: 0;
  }

  .timeline-item {
    padding-left: 2.5rem;
    margin-bottom: 2rem;
  }

  .timeline-content {
    padding: 1.5rem;
  }

  .experience h2 {
    margin-bottom: 2.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .timeline {
    padding: 2rem 0;
  }

  .timeline-item {
    margin-bottom: 2.5rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .timeline {
    padding: 3rem 0;
  }
}
</style>
