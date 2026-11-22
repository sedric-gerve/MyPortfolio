<template>
  <section id="projects" class="projects">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('projectsTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <p class="projects-intro">{{ t('projectsIntro') }}</p>

      <div class="projects-grid">
        <article v-for="(project, index) in projects" :key="project.id" class="project-card">
          <div class="project-ref">{{ ref(index) }}</div>

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
            <a v-if="project.website" :href="project.website" target="_blank" rel="noopener noreferrer" class="link">{{ t('viewProject') }}</a>
            <a v-if="project.github" :href="project.github" target="_blank" rel="noopener noreferrer" class="link">{{ t('github') }}</a>
          </div>
        </article>
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
    const ref = (index) => `P-${String(index + 1).padStart(2, '0')}`
    return {
      t,
      ref,
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
        },
        {
          id: 5,
          name: 'aiFreelanceWatchName',
          description: 'aiFreelanceWatchDesc',
          icon: '⚡',
          technologies: ['n8n', 'Tavily API', 'Google Gemini', 'Gmail', 'AI Agents', 'Automation'],
          images: [
            { src: '/ai-freelance-n8n.png', alt: 'Automated AI freelance opportunity search workflow in n8n' },
            { src: '/ai-freelance-gmail.png', alt: 'Email containing filtered AI freelance opportunities' }
          ]
        },
        {
          id: 6,
          name: 'invoiceAutomationName',
          description: 'invoiceAutomationDesc',
          icon: '🧾',
          technologies: ['n8n', 'Claude', 'MySQL', 'IMAP/SMTP', 'Human-in-the-Loop'],
          images: [
            { src: '/invoice-automation-workflow.png', alt: 'n8n invoice intake workflow with Claude extraction and validation checks' },
            { src: '/invoice-automation-approval.png', alt: 'Human approval email for an invoice that needs review' },
            { src: '/invoice-automation-digest.png', alt: 'Automated weekly digest email of overdue invoices' }
          ]
        },
        {
          id: 7,
          name: 'supportAgentName',
          description: 'supportAgentDesc',
          icon: '🎧',
          technologies: ['n8n', 'PostgreSQL', 'pgvector', 'Voyage AI', 'Claude', 'RAG'],
          images: [
            { src: '/support-agent-workflow.png', alt: 'n8n customer support RAG workflow with similarity search and Claude reply drafting' },
            { src: '/support-agent-reply.png', alt: 'Automatic support reply answered from the knowledge base' },
            { src: '/support-agent-escalation.png', alt: 'Escalation email sent to a human for an out-of-scope question' }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.projects {
  background: var(--primary-color);
  position: relative;
}

.projects::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.projects-intro {
  color: var(--text-on-dark-muted);
  font-size: 1.05rem;
  max-width: 560px;
  margin-top: -2.5rem;
  margin-bottom: 3.5rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(340px, 1fr));
  gap: 2rem;
}

.project-card {
  background: var(--paper);
  border: 1px solid var(--line-on-paper);
  border-radius: 4px;
  padding: 2rem;
  position: relative;
  transition: border-color 0.2s ease;
}

.project-card:hover {
  border-color: var(--accent-color);
}

.project-ref {
  font-family: var(--font-display);
  font-size: 0.8rem;
  font-weight: 600;
  color: var(--accent-color);
  margin-bottom: 1rem;
}

.project-image {
  font-size: 3rem;
  margin-bottom: 1.2rem;
  display: inline-block;
}

.project-gallery {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.5rem;
  margin-bottom: 1.2rem;
}

.project-gallery-link {
  display: block;
  overflow: hidden;
  border: 1px solid var(--line-on-paper);
  border-radius: 2px;
  aspect-ratio: 16 / 10;
  background: var(--paper-muted);
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
  border-radius: 2px;
  background: #111827;
  object-fit: cover;
}

.project-card h3 {
  font-family: var(--font-display);
  color: var(--ink-on-paper);
  margin-bottom: 0.6rem;
  font-size: 1.3rem;
}

.project-description {
  color: var(--text-light);
  margin-bottom: 1.4rem;
  line-height: 1.65;
  font-size: 0.93rem;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1.6rem;
}

.tech-tag {
  color: var(--secondary-color);
  background: transparent;
  padding: 0.25rem 0.6rem;
  border-radius: 2px;
  font-size: 0.76rem;
  font-weight: 500;
  border: 1px solid var(--line-on-paper);
}

.project-links {
  display: flex;
  gap: 1.5rem;
  border-top: 1px solid var(--line-on-paper);
  padding-top: 1.2rem;
}

.link {
  color: var(--ink-on-paper);
  font-weight: 600;
  font-size: 0.9rem;
  position: relative;
}

.link::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 100%;
  height: 1px;
  background: var(--accent-color);
  transform: scaleX(0);
  transform-origin: right;
  transition: transform 0.2s ease;
}

.link:hover {
  color: var(--accent-color);
}

.link:hover::after {
  transform: scaleX(1);
  transform-origin: left;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .projects-intro {
    margin-top: 0;
    margin-bottom: 2rem;
  }

  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.2rem;
  }

  .project-card {
    padding: 1.4rem;
  }

  .project-card h3 {
    font-size: 1.1rem;
  }

  .project-description {
    font-size: 0.88rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .projects-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .projects-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}
</style>
