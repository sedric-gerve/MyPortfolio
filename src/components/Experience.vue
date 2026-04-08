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
          title: 'fullStackDeveloper',
          company: 'freelanceClients',
          date: 'yearsExperience',
          description: 'experienceDesc1'
        },
        {
          id: 2,
          title: 'notableProjects',
          company: 'portfolio',
          date: 'yearsPortfolio',
          description: 'experienceDesc2'
        },
        {
          id: 3,
          title: 'technicalExpertise',
          company: 'coreSkills',
          date: 'yearsCareer',
          description: 'experienceDesc3'
        }
      ]
    }
  }
}
</script>

<style scoped>
.experience {
  background-color: var(--bg-light);
}

.experience h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.timeline {
  position: relative;
  padding: 2rem 0;
}

.timeline::before {
  content: '';
  position: absolute;
  left: 50%;
  transform: translateX(-50%);
  width: 2px;
  height: 100%;
  background-color: var(--secondary-color);
}

.timeline-item {
  margin-bottom: 2rem;
  position: relative;
}

.timeline-item:nth-child(odd) .timeline-content {
  margin-left: 0;
  margin-right: 52%;
}

.timeline-item:nth-child(even) .timeline-content {
  margin-left: 52%;
  margin-right: 0;
}

.timeline-marker {
  position: absolute;
  left: 50%;
  top: 0;
  transform: translateX(-50%);
  width: 15px;
  height: 15px;
  background-color: var(--secondary-color);
  border: 3px solid var(--bg-light);
  border-radius: 50%;
  z-index: 1;
}

.timeline-content {
  background: var(--white);
  padding: 1.5rem;
  border-radius: 8px;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.timeline-content h3 {
  color: var(--primary-color);
  margin-bottom: 0.3rem;
}

.company {
  color: var(--secondary-color);
  font-weight: 600;
  margin-bottom: 0.3rem;
}

.date {
  color: var(--text-light);
  font-size: 0.9rem;
  margin-bottom: 0.5rem;
}

.description {
  color: var(--text-light);
}

@media (max-width: 768px) {
  .timeline::before {
    display: none;
  }

  .timeline-item:nth-child(odd) .timeline-content,
  .timeline-item:nth-child(even) .timeline-content {
    margin-left: 0;
    margin-right: 0;
  }

  .timeline-marker {
    left: 0;
    top: 0;
  }

  .timeline-item {
    padding-left: 2rem;
  }
}
</style>
