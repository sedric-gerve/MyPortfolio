<template>
  <nav class="navbar">
    <div class="container navbar-container">
      <div class="logo">Sedric Gerve Kouam</div>
      <ul class="nav-links">
        <li><a href="#about">{{ t('about') }}</a></li>
        <li><a href="#skills">{{ t('skills') }}</a></li>
        <li><a href="#experience">{{ t('experiences') }}</a></li>
        <li><a href="#projects">{{ t('projects') }}</a></li>
        <li><a href="#blog">{{ t('blog') }}</a></li>
        <li><a href="#contact" class="cta-button">{{ t('contact') }}</a></li>
        <li class="language-switcher">
          <button 
            @click="toggleLanguage" 
            :class="['lang-btn', { active: locale === 'en' }]"
          >
            EN
          </button>
          <button 
            @click="toggleLanguage" 
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
    
    const toggleLanguage = () => {
      const newLocale = locale.value === 'en' ? 'fr' : 'en'
      setLocale(newLocale)
    }
    
    return { t, locale, toggleLanguage }
  }
}
</script>

<style scoped>
.navbar {
  background-color: var(--white);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  position: sticky;
  top: 0;
  z-index: 100;
}

.navbar-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 0;
}

.logo {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
}

.nav-links {
  list-style: none;
  display: flex;
  gap: 2rem;
  align-items: center;
}

.nav-links a {
  color: var(--text-dark);
  font-weight: 500;
  transition: color 0.3s;
}

.nav-links a:hover {
  color: var(--secondary-color);
}

.cta-button {
  background-color: var(--secondary-color);
  color: var(--white) !important;
  padding: 0.5rem 1.5rem;
  border-radius: 5px;
  transition: background-color 0.3s;
}

.cta-button:hover {
  background-color: var(--accent-color);
  color: var(--white) !important;
}

@media (max-width: 768px) {
  .nav-links {
    gap: 1rem;
    font-size: 0.9rem;
  }
}

.language-switcher {
  display: flex;
  gap: 0.3rem;
  margin-left: 1rem;
}

.lang-btn {
  background-color: transparent;
  color: var(--text-dark);
  padding: 0.4rem 0.8rem;
  border: 1px solid var(--text-dark);
  border-radius: 4px;
  font-weight: 600;
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.3s;
}

.lang-btn.active {
  background-color: var(--secondary-color);
  color: var(--white);
  border-color: var(--secondary-color);
}

.lang-btn:hover {
  border-color: var(--secondary-color);
  color: var(--secondary-color);
}
</style>
