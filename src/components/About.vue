<template>
  <section id="about" class="about">
    <div class="container">
      <h2>{{ t('aboutTitle') }}</h2>
      <div class="about-content">
        <div class="about-text">
          <p>{{ t('aboutText1') }}</p>
          <p>{{ t('aboutText2') }}</p>
          <div class="quick-facts">
            <h3>{{ t('quickFactsTitle') }}</h3>
            <ul>
              <li><span class="fact-label">{{ t('factLocationLabel') }}</span>{{ t('factLocationValue') }}</li>
              <li><span class="fact-label">{{ t('factLanguagesLabel') }}</span>{{ t('factLanguagesValue') }}</li>
              <li><span class="fact-label">{{ t('factInterestsLabel') }}</span>{{ t('factInterestsValue') }}</li>
            </ul>
          </div>
        </div>
        <div class="about-image">
          <div class="placeholder-image">
            <img
              src="/person_3.jpg"
              alt="Photo de Sedric Gerve Kouam"
              style="width: 260px; height: 260px; object-fit: cover; border-radius: 12px; box-shadow: 0 4px 16px rgba(30,64,175,0.15); border: 4px solid var(--white);"
            >
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'About',
  setup() {
    const t = inject('t')
    return { t }
  }
}
</script>

<style scoped>
.about {
  background-color: var(--bg-light);
}

.about h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}

.about-text p {
  font-size: 1.1rem;
  color: var(--text-light);
  margin-bottom: 1rem;
  line-height: 1.8;
}

.quick-facts {
  margin-top: 1.5rem;
  background: var(--white);
  border-left: 4px solid var(--secondary-color);
  border-radius: 8px;
  padding: 1.2rem 1.5rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
}

.quick-facts h3 {
  color: var(--primary-color);
  font-size: 1.1rem;
  margin-bottom: 0.8rem;
}

.quick-facts ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 0.6rem;
}

.quick-facts li {
  color: var(--text-light);
  font-size: 0.95rem;
  line-height: 1.5;
}

.fact-label {
  display: block;
  color: var(--secondary-color);
  font-weight: 600;
  font-size: 0.8rem;
  text-transform: uppercase;
  letter-spacing: 0.04em;
  margin-bottom: 0.1rem;
}

.placeholder-image {
  background: var(--secondary-color);
  color: var(--white);
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem 0;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
  }
}
</style>
