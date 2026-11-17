<template>
  <section id="skills" class="skills">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('skillsTitle') }}</h2>
        <span class="rule"></span>
      </div>

      <div v-for="group in skillGroups" :key="group.id" class="skill-group">
        <h3 class="group-title">{{ t(group.title) }}</h3>
        <div class="skills-list">
          <div class="skill-row" v-for="skill in group.skills" :key="skill.id">
            <span class="skill-icon">{{ skill.icon }}</span>
            <div class="skill-body">
              <h4>{{ t(skill.name) }}</h4>
              <p>{{ t(skill.description) }}</p>
              <div class="skill-tags">
                <span v-for="tag in skill.tags" :key="tag" class="tag">{{ tag }}</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Skills',
  setup() {
    const t = inject('t')
    return {
      t,
      skillGroups: [
        {
          id: 'tech',
          title: 'techSkillsGroup',
          skills: [
            {
              id: 1,
              name: 'frontendDevelopment',
              description: 'frontendDescription',
              icon: '🎨',
              tags: ['Vue.js', 'Alpine.js', 'Tailwind CSS', 'HTML5', 'CSS3', 'JavaScript']
            },
            {
              id: 2,
              name: 'backendDevelopment',
              description: 'backendDescription',
              icon: '⚙️',
              tags: ['PHP (Laravel)', 'Livewire', 'Node.js', 'REST APIs']
            },
            {
              id: 3,
              name: 'databaseDesign',
              description: 'databaseDescription',
              icon: '📊',
              tags: ['MySQL', 'Database Design', 'Query Optimization']
            },
            {
              id: 4,
              name: 'devTools',
              description: 'devToolsDescription',
              icon: '🛠️',
              tags: ['Git/GitHub', 'LLM API Integration', 'VS Code', 'Label Studio']
            }
          ]
        },
        {
          id: 'ai',
          title: 'aiSkillsGroup',
          skills: [
            {
              id: 5,
              name: 'promptEngineering',
              description: 'promptEngineeringDescription',
              icon: '✨',
              tags: ['Prompt Design', 'Fine-Tuning', 'Model Evaluation', 'LLMs']
            },
            {
              id: 6,
              name: 'dataLabeling',
              description: 'dataLabelingDescription',
              icon: '🏷️',
              tags: ['Data Labeling', 'Annotation', 'Label Studio', 'AI Training Data']
            },
            {
              id: 7,
              name: 'hitlQa',
              description: 'hitlQaDescription',
              icon: '🔍',
              tags: ['Human-in-the-Loop', 'Data Quality', 'AI Validation', 'QA']
            },
            {
              id: 8,
              name: 'analyticalRigor',
              description: 'analyticalRigorDescription',
              icon: '📐',
              tags: ['Mathematics', 'Fact-Checking', 'Scientific Analysis']
            }
          ]
        }
      ]
    }
  }
}
</script>

<style scoped>
.skills {
  background: var(--primary-color);
  position: relative;
}

.skills::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.skill-group {
  margin-bottom: 3rem;
}

.skill-group:last-child {
  margin-bottom: 0;
}

.group-title {
  font-size: 1.05rem;
  margin-bottom: 1.5rem;
  color: var(--text-on-dark-muted);
  font-weight: 600;
}

.skills-list {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0;
  border-top: 1px solid var(--line-on-ink);
}

.skill-row {
  display: flex;
  gap: 1rem;
  padding: 1.5rem 1rem 1.5rem 0;
  border-bottom: 1px solid var(--line-on-ink);
}

.skill-row:nth-child(odd) {
  border-right: 1px solid var(--line-on-ink);
  padding-right: 1.5rem;
}

.skill-row:nth-child(even) {
  padding-left: 1.5rem;
}

.skill-icon {
  font-size: 1.6rem;
  line-height: 1;
  flex-shrink: 0;
}

.skill-body h4 {
  color: var(--white);
  margin-bottom: 0.4rem;
  font-size: 1.05rem;
}

.skill-body p {
  color: var(--text-on-dark-muted);
  margin-bottom: 0.9rem;
  font-size: 0.9rem;
  line-height: 1.55;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.tag {
  color: var(--accent-color);
  padding: 0.15rem 0;
  font-size: 0.78rem;
  font-weight: 500;
}

.tag:not(:last-child)::after {
  content: '·';
  margin-left: 0.5rem;
  color: var(--line-on-ink);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .skills-list {
    grid-template-columns: 1fr;
  }

  .skill-row,
  .skill-row:nth-child(odd),
  .skill-row:nth-child(even) {
    padding: 1.2rem 0;
    border-right: none;
  }

  .skill-body h4 {
    font-size: 0.95rem;
  }

  .skill-body p {
    font-size: 0.85rem;
  }

  .group-title {
    font-size: 0.95rem;
    margin-bottom: 1rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .skills-list {
    grid-template-columns: 1fr;
  }

  .skill-row:nth-child(odd) {
    border-right: none;
    padding-right: 0;
  }

  .skill-row:nth-child(even) {
    padding-left: 0;
  }
}
</style>
