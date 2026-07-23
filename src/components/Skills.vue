<template>
  <section id="skills" class="skills">
    <div class="container">
      <h2>{{ t('skillsTitle') }}</h2>

      <div v-for="group in skillGroups" :key="group.id" class="skill-group">
        <h3 class="group-title">{{ t(group.title) }}</h3>
        <div class="skills-grid">
          <div class="skill-card" v-for="skill in group.skills" :key="skill.id">
            <div class="skill-icon">{{ skill.icon }}</div>
            <h3>{{ t(skill.name) }}</h3>
            <p>{{ t(skill.description) }}</p>
            <div class="skill-tags">
              <span v-for="tag in skill.tags" :key="tag" class="tag">{{ tag }}</span>
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
  background: linear-gradient(180deg, var(--white) 0%, var(--bg-light) 100%);
  position: relative;
}

.skills::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.skills h2 {
  text-align: center;
  margin-bottom: 4rem;
  animation: fadeInUp 0.7s ease-out;
}

.skill-group {
  margin-bottom: 4.5rem;
}

.skill-group:last-child {
  margin-bottom: 0;
}

.group-title {
  text-align: center;
  font-size: 1.5rem;
  margin-bottom: 2.5rem;
  position: relative;
  display: inline-block;
  left: 50%;
  transform: translateX(-50%);
  padding-bottom: 1rem;
  color: var(--primary-color);
  font-weight: 700;
}

.group-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 60px;
  height: 4px;
  background: linear-gradient(90deg, var(--secondary-color), var(--accent-color));
  border-radius: 2px;
  box-shadow: 0 2px 8px rgba(37, 99, 235, 0.3);
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 2.5rem;
}

.skill-card {
  background: var(--white);
  padding: 2.5rem 2rem;
  border-radius: 12px;
  text-align: center;
  transition: all 0.3s ease;
  border: 1px solid var(--bg-light);
  position: relative;
  overflow: hidden;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  animation: fadeInUp 0.7s ease-out both;
}

.skill-card:nth-child(1) { animation-delay: 0.1s; }
.skill-card:nth-child(2) { animation-delay: 0.2s; }
.skill-card:nth-child(3) { animation-delay: 0.3s; }
.skill-card:nth-child(4) { animation-delay: 0.4s; }
.skill-card:nth-child(5) { animation-delay: 0.5s; }
.skill-card:nth-child(6) { animation-delay: 0.6s; }

.skill-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--secondary-color), var(--accent-color));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.skill-card:hover::before {
  transform: scaleX(1);
}

.skill-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 30px rgba(37, 99, 235, 0.15);
  border-color: var(--secondary-color);
}

.skill-icon {
  font-size: 3.5rem;
  margin-bottom: 1.2rem;
  transition: transform 0.3s ease;
  display: inline-block;
}

.skill-card:hover .skill-icon {
  transform: scale(1.15) rotate(5deg);
}

.skill-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.8rem;
  font-size: 1.25rem;
}

.skill-card p {
  color: var(--text-light);
  margin-bottom: 1.5rem;
  font-size: 0.95rem;
  line-height: 1.6;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.6rem;
  justify-content: center;
}

.tag {
  background: linear-gradient(135deg, rgba(37, 99, 235, 0.1) 0%, rgba(122, 58, 237, 0.1) 100%);
  color: var(--secondary-color);
  padding: 0.4rem 1rem;
  border-radius: 20px;
  font-size: 0.8rem;
  font-weight: 500;
  border: 1px solid rgba(37, 99, 235, 0.2);
  transition: all 0.3s ease;
}

.skill-card:hover .tag {
  background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
  color: var(--white);
  border-color: transparent;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .skill-card {
    padding: 1.5rem 1rem;
    margin-bottom: 0.5rem;
  }

  .skill-icon {
    font-size: 2.5rem;
    margin-bottom: 0.8rem;
  }

  .skill-card h3 {
    font-size: 1rem;
    margin-bottom: 0.5rem;
  }

  .skill-card p {
    font-size: 0.85rem;
    margin-bottom: 1rem;
  }

  .tag {
    font-size: 0.7rem;
    padding: 0.3rem 0.6rem;
  }

  .group-title {
    font-size: 1.1rem;
    margin-bottom: 1.5rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .skills-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .skill-card {
    padding: 1.8rem 1.3rem;
  }

  .group-title {
    font-size: 1.25rem;
    margin-bottom: 2rem;
  }

  .skills h2 {
    margin-bottom: 2.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .skills-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .skills-grid {
    grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  }
}
</style>
