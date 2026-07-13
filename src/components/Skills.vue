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
  background-color: var(--white);
}

.skills h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.skill-group {
  margin-bottom: 3rem;
}

.skill-group:last-child {
  margin-bottom: 0;
}

.group-title {
  text-align: center;
  color: var(--secondary-color);
  font-size: 1.4rem;
  margin-bottom: 1.8rem;
  position: relative;
  display: inline-block;
  left: 50%;
  transform: translateX(-50%);
  padding-bottom: 0.5rem;
}

.group-title::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
  width: 50px;
  height: 3px;
  background-color: var(--secondary-color);
  border-radius: 2px;
}

.skills-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.skill-card {
  background: var(--bg-light);
  padding: 2rem;
  border-radius: 10px;
  text-align: center;
  transition: transform 0.3s, box-shadow 0.3s;
}

.skill-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.skill-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.skill-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
}

.skill-card p {
  color: var(--text-light);
  margin-bottom: 1rem;
}

.skill-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  justify-content: center;
}

.tag {
  background-color: var(--secondary-color);
  color: var(--white);
  padding: 0.3rem 0.8rem;
  border-radius: 20px;
  font-size: 0.85rem;
}
</style>
