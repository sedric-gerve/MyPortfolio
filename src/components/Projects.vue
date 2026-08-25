<template>
  <section id="projects" class="projects">
    <div class="container">
      <h2>{{ t('projectsTitle') }}</h2>
      <div class="projects-grid">
        <div v-for="project in projects" :key="project.id" class="project-card">
          <div v-if="project.images" class="project-gallery">
            <a
              v-for="image in project.images"
              :key="image.src"
              :href="image.src"
              target="_blank"
              rel="noopener noreferrer"
              class="project-gallery-link"
            >
              <img :src="image.src" :alt="image.alt" class="project-gallery-image">
            </a>
          </div>
          <div v-else class="project-image">{{ project.icon }}</div>
          <video v-if="project.video" controls preload="metadata" class="project-video">
            <source :src="project.video" type="video/mp4">
          </video>
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
        },
        {
          id: 4,
          name: 'aiRagCrmName',
          description: 'aiRagCrmDesc',
          icon: '🤖',
          website: 'https://ai-rag-crm.onrender.com/admin/',
          technologies: ['Laravel', 'Filament', 'PostgreSQL', 'RAG', 'Voyage AI', 'Claude'],
          images: [
            { src: '/ai-rag-crm-clients.png', alt: 'AI RAG CRM client management screen' },
            { src: '/ai-rag-crm-opportunities.png', alt: 'AI RAG CRM sales opportunities screen' },
            { src: '/ai-rag-crm-assistant.png', alt: 'AI RAG CRM AI assistant screen' }
          ],
          video: '/demo-video.mp4'
        }
      ]
    }
  }
}
</script>

<style scoped>
.projects {
  background: linear-gradient(180deg, var(--bg-lighter) 0%, var(--white) 100%);
  position: relative;
}

.projects::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.projects h2 {
  text-align: center;
  margin-bottom: 4rem;
  animation: fadeInUp 0.7s ease-out;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2.5rem;
}

.project-card {
  background: var(--white);
  border: 1px solid var(--bg-light);
  border-radius: 14px;
  padding: 2.5rem 2rem;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  animation: fadeInUp 0.7s ease-out both;
}

.project-card:nth-child(1) { animation-delay: 0.1s; }
.project-card:nth-child(2) { animation-delay: 0.2s; }
.project-card:nth-child(3) { animation-delay: 0.3s; }

.project-card::before {
  content: '';
  position: absolute;
  top: -100%;
  left: -100%;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.15) 0%, transparent 70%);
  transition: all 0.5s ease;
}

.project-card:hover::before {
  top: -30%;
  left: -30%;
}

.project-card:hover {
  transform: translateY(-12px);
  box-shadow: 0 15px 40px rgba(37, 99, 235, 0.15);
  border-color: var(--secondary-color);
}

.project-image {
  font-size: 3.5rem;
  margin-bottom: 1.2rem;
  display: inline-block;
  transition: transform 0.3s ease;
}

.project-gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.5rem;
  margin-bottom: 1.2rem;
  position: relative;
  z-index: 1;
}

.project-gallery-link {
  display: block;
  overflow: hidden;
  border: 1px solid var(--bg-light);
  border-radius: 6px;
  aspect-ratio: 16 / 10;
  background: var(--bg-lighter);
}

.project-gallery-image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
  transition: transform 0.3s ease;
}

.project-gallery-link:hover .project-gallery-image {
  transform: scale(1.06);
}

.project-video {
  width: 100%;
  aspect-ratio: 16 / 9;
  display: block;
  margin-bottom: 1.2rem;
  border-radius: 8px;
  background: #111827;
  object-fit: cover;
  position: relative;
  z-index: 1;
}

.project-card:hover .project-image {
  transform: scale(1.2) rotate(-5deg);
}

.project-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.8rem;
  font-size: 1.4rem;
  position: relative;
  z-index: 1;
}

.project-description {
  color: var(--text-light);
  margin-bottom: 1.5rem;
  line-height: 1.7;
  font-size: 0.95rem;
  position: relative;
  z-index: 1;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  margin-bottom: 1.8rem;
  position: relative;
  z-index: 1;
}

.tech-tag {
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.1) 0%, rgba(122, 58, 237, 0.1) 100%);
  color: var(--secondary-color);
  padding: 0.4rem 0.9rem;
  border-radius: 18px;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid rgba(37, 99, 235, 0.2);
  transition: all 0.3s ease;
}

.project-card:hover .tech-tag {
  background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
  color: var(--white);
  border-color: transparent;
}

.project-links {
  display: flex;
  gap: 1.5rem;
  position: relative;
  z-index: 1;
}

.link {
  color: var(--secondary-color);
  font-weight: 600;
  font-size: 0.95rem;
  transition: all 0.3s ease;
  position: relative;
  display: inline-flex;
  align-items: center;
  gap: 0.4rem;
}

.link::after {
  content: '→';
  transition: transform 0.3s ease;
}

.link:hover {
  color: var(--accent-color);
}

.link:hover::after {
  transform: translateX(4px);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .project-card {
    padding: 1.5rem 1rem;
  }

  .project-image {
    font-size: 2.5rem;
    margin-bottom: 0.8rem;
  }

  .project-card h3 {
    font-size: 1.1rem;
    margin-bottom: 0.5rem;
  }

  .project-description {
    font-size: 0.85rem;
    margin-bottom: 1rem;
  }

  .tech-tag {
    font-size: 0.7rem;
    padding: 0.3rem 0.6rem;
  }

  .link {
    font-size: 0.85rem;
  }

  .projects h2 {
    margin-bottom: 2rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .project-card {
    padding: 1.8rem 1.3rem;
  }

  .projects h2 {
    margin-bottom: 2.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .projects-grid {
    grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  }
}
</style>
