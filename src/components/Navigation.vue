<template>
  <nav class="navbar">
    <div class="container navbar-container">
      <div class="logo">Sedric Gerve Kouam</div>
      <ul class="nav-links">
        <li><a href="#about">{{ t('about') }}</a></li>
        <li><a href="#skills">{{ t('skills') }}</a></li>
        <li><a href="#experience">{{ t('experiences') }}</a></li>
        <li><a href="#projects">{{ t('projects') }}</a></li>
        <li><a href="#certifications">{{ t('certifications') }}</a></li>
        <li><a href="#contact" class="cta-button">{{ t('contact') }}</a></li>
        <li class="language-switcher">
          <button
            @click="setLanguage('en')"
            :class="['lang-btn', { active: locale === 'en' }]"
          >
            EN
          </button>
          <button
            @click="setLanguage('fr')"
            :class="['lang-btn', { active: locale === 'fr' }]"
          >
            FR
          </button>
        </li>
      </ul>
    </div>
  </nav>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Navigation',
  setup() {
    const t = inject('t')
    const locale = inject('locale')
    const setLocale = inject('setLocale')
    
    const setLanguage = (newLocale) => {
      setLocale(newLocale)
    }

    return { t, locale, setLanguage }
  }
}
</script>

<style scoped>
.navbar {
  background-color: var(--white);
  box-shadow: 0 2px 20px rgba(0, 0, 0, 0.08);
  position: sticky;
  top: 0;
  z-index: 100;
  backdrop-filter: blur(10px);
  background-color: rgba(255, 255, 255, 0.98);
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.2rem 0;
  max-width: 1200px;
  margin: 0 auto;
  padding-left: 20px;
  padding-right: 20px;
}

.logo {
  font-size: 1.4rem;
  font-weight: 800;
  background: linear-gradient(135deg, var(--primary-color), var(--accent-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  letter-spacing: -0.5px;
  transition: transform 0.3s ease;
}

.logo:hover {
  transform: scale(1.05);
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 2.5rem;
  align-items: center;
}

.nav-links a {
  color: var(--text-dark);
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  font-size: 0.95rem;
}

.nav-links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--secondary-color), var(--accent-color));
  transition: width 0.3s ease;
}

.nav-links a:hover {
  color: var(--secondary-color);
}

.nav-links a:hover::after {
  width: 100%;
}

.cta-button {
  background: linear-gradient(135deg, var(--secondary-color) 0%, var(--accent-color) 100%);
  color: var(--white) !important;
  padding: 0.65rem 1.8rem;
  border-radius: 8px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(37, 99, 235, 0.3);
  font-weight: 600;
}

.cta-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.4);
  color: var(--white) !important;
}

.cta-button::after {
  display: none;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .navbar-container {
    padding: 0.8rem 0;
  }

  .logo {
    font-size: 0.95rem;
  }

  .nav-links {
    gap: 0.6rem;
    font-size: 0.75rem;
  }

  .language-switcher {
    margin-left: 0.5rem;
    padding-left: 0.5rem;
  }

  .lang-btn {
    padding: 0.3rem 0.6rem;
    font-size: 0.7rem;
  }

  .cta-button {
    padding: 0.5rem 1rem;
    font-size: 0.8rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .navbar-container {
    padding: 1rem 0;
  }

  .nav-links {
    gap: 1.2rem;
    font-size: 0.85rem;
  }

  .logo {
    font-size: 1.1rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .navbar-container {
    max-width: 1400px;
  }
}

.language-switcher {
  display: flex;
  gap: 0.4rem;
  margin-left: 1rem;
  padding-left: 1rem;
  border-left: 2px solid var(--bg-light);
}

.lang-btn {
  background-color: transparent;
  color: var(--text-dark);
  padding: 0.4rem 0.8rem;
  border: 1.5px solid var(--text-light);
  border-radius: 6px;
  font-weight: 600;
  font-size: 0.8rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.lang-btn.active {
  background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
  color: var(--white);
  border-color: transparent;
  box-shadow: 0 4px 12px rgba(37, 99, 235, 0.3);
}

.lang-btn:hover:not(.active) {
  border-color: var(--secondary-color);
  color: var(--secondary-color);
  background-color: rgba(37, 99, 235, 0.05);
}
</style>
