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
              src="/IMG_20260215_145501_378-1.jpg"
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
  background: linear-gradient(180deg, var(--white) 0%, var(--bg-light) 100%);
  position: relative;
}

.about::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.about h2 {
  text-align: center;
  margin-bottom: 4rem;
  animation: fadeInUp 0.7s ease-out;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
}

.about-text {
  animation: slideInLeft 0.8s ease-out;
}

.about-text p {
  font-size: 1.05rem;
  color: var(--text-light);
  margin-bottom: 1.5rem;
  line-height: 1.9;
}

.quick-facts {
  margin-top: 2rem;
  background: var(--white);
  border-left: 5px solid var(--secondary-color);
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.1);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.quick-facts::before {
  content: '';
  position: absolute;
  top: 0;
  right: -100px;
  width: 200px;
  height: 200px;
  background: radial-gradient(circle, rgba(37, 99, 235, 0.08) 0%, transparent 70%);
  border-radius: 50%;
  pointer-events: none;
}

.quick-facts:hover {
  transform: translateY(-2px);
  box-shadow: 0 12px 35px rgba(37, 99, 235, 0.15);
}

.quick-facts h3 {
  color: var(--primary-color);
  font-size: 1.2rem;
  margin-bottom: 1.2rem;
  font-weight: 700;
  position: relative;
  z-index: 1;
}

.quick-facts ul {
  list-style: none;
  display: flex;
  flex-direction: column;
  gap: 1rem;
  position: relative;
  z-index: 1;
}

.quick-facts li {
  color: var(--text-light);
  font-size: 0.95rem;
  line-height: 1.6;
}

.fact-label {
  display: block;
  color: var(--secondary-color);
  font-weight: 700;
  font-size: 0.75rem;
  text-transform: uppercase;
  letter-spacing: 0.08em;
  margin-bottom: 0.3rem;
}

.placeholder-image {
  animation: slideInRight 0.8s ease-out;
  border-radius: 12px;
  overflow: hidden;
}

.placeholder-image img {
  transition: transform 0.4s ease;
  box-shadow: 0 15px 40px rgba(37, 99, 235, 0.2);
}

.placeholder-image:hover img {
  transform: scale(1.05);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .about-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .about h2 {
    margin-bottom: 2rem;
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

  .about h2 {
    margin-bottom: 2.5rem;
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
