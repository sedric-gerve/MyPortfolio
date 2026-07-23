<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <p>{{ t('footerCopyright') }}</p>
        <div class="footer-links">
          <a href="#about">{{ t('about') }}</a>
          <a href="#projects">{{ t('projects') }}</a>
          <a href="#certifications">{{ t('certifications') }}</a>
          <a href="#contact">{{ t('contact') }}</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'Footer',
  setup() {
    const t = inject('t')
    return { t }
  }
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, var(--primary-color) 0%, var(--secondary-color) 100%);
  color: var(--white);
  text-align: center;
  padding: 3.5rem 0 2rem;
  position: relative;
  overflow: hidden;
}

.footer::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.3), transparent);
}

.footer::after {
  content: '';
  position: absolute;
  bottom: -100px;
  left: -100px;
  width: 400px;
  height: 400px;
  background: radial-gradient(circle, rgba(255, 255, 255, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  pointer-events: none;
}

.container {
  position: relative;
  z-index: 2;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 2rem;
}

.footer-content p {
  margin: 0;
  font-size: 0.95rem;
  color: rgba(255, 255, 255, 0.85);
  font-weight: 500;
}

.footer-links {
  display: flex;
  gap: 2.5rem;
  flex-wrap: wrap;
  justify-content: flex-end;
}

.footer-links a {
  color: rgba(255, 255, 255, 0.85);
  transition: all 0.3s ease;
  position: relative;
  font-weight: 500;
  font-size: 0.95rem;
}

.footer-links a::after {
  content: '';
  position: absolute;
  bottom: -4px;
  left: 0;
  width: 0;
  height: 2px;
  background: var(--white);
  transition: width 0.3s ease;
}

.footer-links a:hover {
  color: var(--white);
}

.footer-links a:hover::after {
  width: 100%;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .footer {
    padding: 2rem 0 1.2rem;
  }

  .footer-content {
    flex-direction: column;
    gap: 1rem;
  }

  .footer-links {
    justify-content: center;
    gap: 1rem;
    flex-wrap: wrap;
  }

  .footer-content p {
    font-size: 0.85rem;
  }

  .footer-links a {
    font-size: 0.8rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .footer {
    padding: 2.5rem 0 1.5rem;
  }

  .footer-content {
    flex-direction: column;
    gap: 1.5rem;
  }

  .footer-links {
    justify-content: center;
    gap: 1.5rem;
  }

  .footer-content p {
    font-size: 0.9rem;
  }

  .footer-links a {
    font-size: 0.85rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .footer {
    padding: 3rem 0 2rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .footer {
    padding: 3.5rem 0 2rem;
  }
}
</style>
