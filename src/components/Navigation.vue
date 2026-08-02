<template>
  <nav class="navbar">
    <div class="container navbar-container">
      <div class="logo">Sedric Gerve Kouam</div>

      <button
        class="menu-toggle"
        :class="{ open: isMenuOpen }"
        @click="isMenuOpen = !isMenuOpen"
        :aria-expanded="isMenuOpen"
        aria-label="Toggle navigation menu"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <ul class="nav-links" :class="{ open: isMenuOpen }">
        <li><a href="#about" @click="closeMenu">{{ t('about') }}</a></li>
        <li><a href="#skills" @click="closeMenu">{{ t('skills') }}</a></li>
        <li><a href="#experience" @click="closeMenu">{{ t('experiences') }}</a></li>
        <li><a href="#projects" @click="closeMenu">{{ t('projects') }}</a></li>
        <li><a href="#certifications" @click="closeMenu">{{ t('certifications') }}</a></li>
        <li><a href="#contact" class="cta-button" @click="closeMenu">{{ t('contact') }}</a></li>
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
import { inject, ref } from 'vue'

export default {
  name: 'Navigation',
  setup() {
    const t = inject('t')
    const locale = inject('locale')
    const setLocale = inject('setLocale')
    const isMenuOpen = ref(false)

    const setLanguage = (newLocale) => {
      setLocale(newLocale)
    }

    const closeMenu = () => {
      isMenuOpen.value = false
    }

    return { t, locale, setLanguage, isMenuOpen, closeMenu }
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

.menu-toggle {
  display: none;
  flex-direction: column;
  justify-content: center;
  gap: 5px;
  background: transparent;
  padding: 8px;
  width: 40px;
  height: 40px;
  z-index: 110;
}

.menu-toggle span {
  display: block;
  width: 100%;
  height: 2px;
  background-color: var(--text-dark);
  border-radius: 2px;
  transition: all 0.3s ease;
}

.menu-toggle.open span:nth-child(1) {
  transform: translateY(7px) rotate(45deg);
}

.menu-toggle.open span:nth-child(2) {
  opacity: 0;
}

.menu-toggle.open span:nth-child(3) {
  transform: translateY(-7px) rotate(-45deg);
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

/* Collapsed nav (Phones, phablets, tablets up to 1024px) */
@media (max-width: 1024px) {
  .menu-toggle {
    display: flex;
  }

  .nav-links {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    flex-direction: column;
    align-items: stretch;
    gap: 0;
    background-color: var(--white);
    box-shadow: 0 12px 25px rgba(0, 0, 0, 0.1);
    max-height: 0;
    overflow: hidden;
    opacity: 0;
    transition: max-height 0.3s ease, opacity 0.25s ease;
  }

  .nav-links.open {
    max-height: 500px;
    opacity: 1;
  }

  .nav-links li {
    width: 100%;
  }

  .nav-links a {
    display: block;
    padding: 1rem 20px;
    font-size: 1rem;
  }

  .nav-links a::after {
    display: none;
  }

  .cta-button {
    margin: 0.5rem 20px;
    text-align: center;
  }

  .language-switcher {
    margin: 0.5rem 20px 1rem;
    padding-left: 0;
    border-left: none;
    justify-content: center;
  }
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .navbar-container {
    padding: 0.8rem 0;
  }

  .logo {
    font-size: 0.95rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .navbar-container {
    padding: 1rem 0;
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
