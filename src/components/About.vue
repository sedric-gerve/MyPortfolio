<template>
  <section id="about" class="about">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('aboutTitle') }}</h2>
        <span class="rule"></span>
      </div>
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
              src="/sedric-pic.jpg"
              :alt="t('profilePhotoAlt')"
              class="profile-photo"
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
  background: var(--primary-color);
  position: relative;
}

.about::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: start;
}

.about-text p {
  font-size: 1.05rem;
  color: var(--text-on-dark-muted);
  margin-bottom: 1.5rem;
  line-height: 1.9;
}

.quick-facts {
  margin-top: 2rem;
  background: var(--paper);
  border: 1px solid var(--line-on-paper);
  border-radius: 4px;
  padding: 1.8rem 2rem;
  position: relative;
}

.quick-facts h3 {
  font-family: var(--font-display);
  color: var(--ink-on-paper);
  font-size: 1.05rem;
  margin-bottom: 1.2rem;
  font-weight: 600;
}

.quick-facts ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.quick-facts li {
  color: var(--text-light);
  font-size: 0.95rem;
  line-height: 1.6;
}

.fact-label {
  display: block;
  color: var(--secondary-color);
  font-weight: 600;
  font-size: 0.8rem;
  margin-bottom: 0.2rem;
}

.placeholder-image {
  border: 1px solid var(--line-on-ink);
  border-radius: 4px;
  padding: 10px;
  width: fit-content;
}

.profile-photo {
  width: 260px;
  height: 260px;
  max-width: 100%;
  aspect-ratio: 1 / 1;
  object-fit: cover;
  border-radius: 2px;
  display: block;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .about-text p {
    font-size: 0.95rem;
    margin-bottom: 1rem;
  }

  .quick-facts {
    padding: 1.2rem;
    margin-top: 1rem;
  }

  .quick-facts h3 {
    font-size: 1rem;
    margin-bottom: 0.8rem;
  }

  .quick-facts ul {
    gap: 0.6rem;
  }

  .fact-label {
    font-size: 0.7rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .quick-facts {
    padding: 1.5rem;
    margin-top: 1.5rem;
  }

  .about-text p {
    font-size: 1rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .about-content {
    grid-template-columns: 1fr 0.9fr;
    gap: 3rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .about-content {
    grid-template-columns: 1.1fr 1fr;
  }
}
</style>
