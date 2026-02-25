<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2>Projects</h2>
      <div class="projects-grid">
        <div v-for="project in projects" :key="project.id" class="project-card">
          <div class="project-image">{{ project.icon }}</div>
          <h3>{{ project.name }}</h3>
          <p class="project-description">{{ project.description }}</p>
          <div class="project-tags">
            <span v-for="tech in project.technologies" :key="tech" class="tech-tag">{{ tech }}</span>
          </div>
          <div class="project-links">
            <a href="#" class="link">View Project</a>
            <a href="#" class="link">GitHub</a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Projects',
  data() {
    return {
      projects: [
        {
          id: 1,
          name: 'Gestismart.com',
          description: 'Comprehensive business management solution with invoicing, inventory, and client management. Built with TALL stack for scalability and performance.',
          icon: '💼',
          technologies: ['Laravel', 'Livewire', 'Alpine.js', 'Tailwind CSS', 'MySQL', 'Docker']
        },
        {
          id: 2,
          name: 'Optisales.logiciel.com',
          description: 'Advanced sales optimization platform streamlining sales processes, pipeline management, and performance analytics for businesses.',
          icon: '📈',
          technologies: ['Laravel', 'Livewire', 'Tailwind CSS', 'MySQL', 'Git/GitHub']
        },
        {
          id: 3,
          name: 'SmartBulkMessenger.com',
          description: 'Intelligent bulk messaging service with campaign management, analytics, and API integration for businesses of all sizes.',
          icon: '💬',
          technologies: ['Laravel', 'Alpine.js', 'Tailwind CSS', 'MySQL', 'REST API', 'Docker']
        },
        {
          id: 4,
          name: 'TALL Stack Expertise',
          description: 'Specialized in building reactive web applications using the modern TALL stack with emphasis on performance and user experience.',
          icon: '🏗️',
          technologies: ['Tailwind CSS', 'Alpine.js', 'Livewire', 'Laravel']
        },
        {
          id: 5,
          name: 'Database Architecture',
          description: 'Expert in designing optimized MySQL database schemas for complex business applications and queries.',
          icon: '🗄️',
          technologies: ['MySQL', 'Database Design', 'Query Optimization']
        },
        {
          id: 6,
          name: 'DevOps & Deployment',
          description: 'End-to-end deployment expertise with Docker containerization, Git version control, and infrastructure management.',
          icon: '🚀',
          technologies: ['Docker', 'Git/GitHub', 'CI/CD', 'Linux', 'Deployment']
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
