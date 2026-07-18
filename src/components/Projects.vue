<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2>{{ t('projectsTitle') }}</h2>
      <div class="projects-grid">
        <div v-for="project in projects" :key="project.id" class="project-card">
          <div class="project-image">{{ project.icon }}</div>
          <h3>{{ t(project.name) }}</h3>
          <p class="project-description">{{ t(project.description) }}</p>
          <div class="project-tags">
            <span v-for="tech in project.technologies" :key="tech" class="tech-tag">{{ tech }}</span>
          </div>
          <div class="project-links">
            <a :href="project.website" target="_blank" rel="noopener noreferrer" class="link">{{ t('viewProject') }}</a>
            <a v-if="project.github" :href="project.github" target="_blank" rel="noopener noreferrer" class="link">{{ t('github') }}</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Projects',
  setup() {
    const t = inject('t')
    return {
      t,
      projects: [
        {
          id: 1,
          name: 'gestiSmartName',
          description: 'gestiSmartDesc',
          icon: '💼',
          website: 'https://gestismart.com',
          technologies: ['Laravel', 'Livewire', 'Alpine.js', 'Tailwind CSS', 'MySQL']
        },
        {
          id: 2,
          name: 'optiSalesName',
          description: 'optiSalesDesc',
          icon: '📈',
          website: 'https://optisales.logiciel.cm',
          technologies: ['Laravel', 'Livewire', 'Tailwind CSS', 'MySQL', 'Git/GitHub']
        },
        {
          id: 3,
          name: 'smartBulkName',
          description: 'smartBulkDesc',
          icon: '💬',
          website: 'https://smartbulkmessenger.com',
          technologies: ['Laravel', 'Alpine.js', 'Tailwind CSS', 'MySQL', 'REST API', 'LLM API']
        }
      ]
    }
  }
}
</script>

<style scoped>
.projects {
  background-color: var(--white);
}

.projects h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
}

.project-card {
  background: var(--white);
  border: 1px solid var(--bg-light);
  border-radius: 10px;
  padding: 2rem;
  transition: all 0.3s;
}

.project-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 15px 30px rgba(0, 0, 0, 0.15);
  border-color: var(--secondary-color);
}

.project-image {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.project-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

.project-description {
  color: var(--text-light);
  margin-bottom: 1rem;
  line-height: 1.6;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.tech-tag {
  background: var(--bg-light);
  color: var(--secondary-color);
  padding: 0.3rem 0.7rem;
  border-radius: 15px;
  font-size: 0.85rem;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.link {
  color: var(--secondary-color);
  font-weight: 600;
  transition: color 0.3s;
}

.link:hover {
  color: var(--accent-color);
}
</style>
