<template>
  <div id="app">
    <Navigation />
    <Hero />
    <About />
    <Skills />
    <Experience />
    <Projects />
    <Blog />
    <Contact />
    <Footer />
  </div>
</template>

<script>
import { ref, provide } from 'vue'
import Navigation from './components/Navigation.vue'
import Hero from './components/Hero.vue'
import About from './components/About.vue'
import Skills from './components/Skills.vue'
import Experience from './components/Experience.vue'
import Projects from './components/Projects.vue'
import Blog from './components/Blog.vue'
import Contact from './components/Contact.vue'
import Footer from './components/Footer.vue'
import { useTranslations } from './i18n'

export default {
  name: 'App',
  components: {
    Navigation,
    Hero,
    About,
    Skills,
    Experience,
    Projects,
    Blog,
    Contact,
    Footer
  },
  setup() {
    // Get locale from localStorage or default to 'en'
    const savedLocale = localStorage.getItem('locale') || 'en'
    const locale = ref(savedLocale)
    
    // Watch for changes and save to localStorage
    const setLocale = (newLocale) => {
      locale.value = newLocale
      localStorage.setItem('locale', newLocale)
    }
    
    // Provide locale and translation function to all children
    provide('locale', locale)
    provide('t', (key) => {
      const translations = useTranslations(locale.value)
      return translations[key] || key
    })
    provide('setLocale', setLocale)
    
    return { locale, setLocale }
  }
}
</script>

<style scoped>
#app {
  min-height: 100vh;
}
</style>
