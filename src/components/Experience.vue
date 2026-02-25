<template>
  <section id="experience" class="experience">
    <div class="container">
      <h2>Experience</h2>
      <div class="timeline">
        <div v-for="job in jobs" :key="job.id" class="timeline-item">
          <div class="timeline-marker"></div>
          <div class="timeline-content">
            <h3>{{ job.title }}</h3>
            <p class="company">{{ job.company }}</p>
            <p class="date">{{ job.date }}</p>
            <p class="description">{{ job.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Experience',
  data() {
    return {
      jobs: [
        {
          id: 1,
          title: 'Full Stack Developer',
          company: 'Freelance & Multiple Clients',
          date: '2018 - Present (6+ years)',
          description: 'Specialized in TALL stack development. Built SaaS platforms, enterprise applications, and custom web solutions using Laravel, Livewire, Alpine.js, and Tailwind CSS. Implemented MySQL databases, Docker containerization, and Git-based version control.'
        },
        {
          id: 2,
          title: 'Notable Projects',
          company: 'Portfolio',
          date: '2018 - Present',
          description: 'Developed: Gestismart.com (Business Management Solution), Optisales.logiciel.com (Sales Optimization Platform), SmartBulkMessenger.com (Messaging Service)'
        },
        {
          id: 3,
          title: 'Technical Expertise',
          company: 'Core Skills',
          date: 'Throughout Career',
          description: 'Full-stack development with TALL stack, REST API design, Database architecture with MySQL, Docker containerization, Git/GitHub version control, and clean code best practices.'
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
