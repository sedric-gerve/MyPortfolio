<template>
  <section id="skills" class="skills">
    <div class="container">
      <h2>{{ t('skillsTitle') }}</h2>
      <div class="skills-grid">
        <div class="skill-card" v-for="skill in skills" :key="skill.id">
          <div class="skill-icon">{{ skill.icon }}</div>
          <h3>{{ t(skill.name) }}</h3>
          <p>{{ t(skill.description) }}</p>
          <div class="skill-tags">
            <span v-for="tag in skill.tags" :key="tag" class="tag">{{ tag }}</span>
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
      skills: [
        {
          id: 1,
          name: 'frontendDevelopment',
          description: 'frontendDescription',
          icon: '🎨',
          tags: ['Alpine.js', 'Tailwind CSS', 'JavaScript', 'Responsive Design']
        },
        {
          id: 2,
          name: 'backendDevelopment',
          description: 'backendDescription',
          icon: '⚙️',
          tags: ['Laravel', 'Livewire', 'PHP', 'RESTful APIs']
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
          name: 'devops',
          description: 'devopsDescription',
          icon: '🚀',
          tags: ['Docker', 'Git/GitHub', 'Linux', 'CI/CD']
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
