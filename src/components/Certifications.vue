<template>
  <section id="certifications" class="certifications">
    <div class="container">
      <h2>{{ t('certsTitle') }}</h2>

      <div class="certs-layout">
        <div class="certs-column">
          <h3 class="column-title">{{ t('certsSubtitle') }}</h3>
          <div class="card-list">
            <div v-for="cert in certs" :key="cert.id" class="cert-card">
              <div class="cert-icon">🎓</div>
              <div class="cert-body">
                <h4>{{ t(cert.title) }}</h4>
                <p class="cert-place">{{ t(cert.place) }}</p>
              </div>
              <span class="cert-date">{{ t(cert.date) }}</span>
            </div>
          </div>
        </div>

        <div class="certs-column">
          <h3 class="column-title">{{ t('educationSubtitle') }}</h3>
          <div class="card-list">
            <div v-for="edu in education" :key="edu.id" class="cert-card">
              <div class="cert-icon">🏛️</div>
              <div class="cert-body">
                <h4>{{ t(edu.title) }}</h4>
                <p class="cert-place">{{ t(edu.place) }}</p>
              </div>
              <span class="cert-date">{{ t(edu.date) }}</span>
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
  name: 'Certifications',
  setup() {
    const t = inject('t')
    return {
      t,
      certs: [
        { id: 1, title: 'cert1Title', place: 'cert1Place', date: 'cert1Date' },
        { id: 2, title: 'cert2Title', place: 'cert2Place', date: 'cert2Date' },
        { id: 3, title: 'cert3Title', place: 'cert3Place', date: 'cert3Date' },
        { id: 4, title: 'cert4Title', place: 'cert4Place', date: 'cert4Date' }
      ],
      education: [
        { id: 1, title: 'edu1Title', place: 'edu1Place', date: 'edu1Date' },
        { id: 2, title: 'edu2Title', place: 'edu2Place', date: 'edu2Date' }
      ]
    }
  }
}
</script>

<style scoped>
.certifications {
  background: linear-gradient(180deg, var(--bg-lighter) 0%, var(--white) 100%);
  position: relative;
}

.certifications::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.certifications h2 {
  text-align: center;
  margin-bottom: 4rem;
  animation: fadeInUp 0.7s ease-out;
}

.certs-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3.5rem;
}

.column-title {
  color: var(--primary-color);
  font-size: 1.4rem;
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 3px solid var(--secondary-color);
  font-weight: 700;
  position: relative;
}

.column-title::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 40px;
  height: 3px;
  background: linear-gradient(90deg, var(--secondary-color), var(--accent-color));
  border-radius: 2px;
}

.card-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.cert-card {
  background: var(--white);
  border-radius: 12px;
  padding: 1.8rem;
  display: flex;
  align-items: flex-start;
  gap: 1.5rem;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
  border: 1px solid var(--bg-light);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  animation: fadeInUp 0.7s ease-out both;
}

.cert-card:nth-child(1) { animation-delay: 0.1s; }
.cert-card:nth-child(2) { animation-delay: 0.2s; }
.cert-card:nth-child(3) { animation-delay: 0.3s; }
.cert-card:nth-child(4) { animation-delay: 0.4s; }
.cert-card:nth-child(5) { animation-delay: 0.5s; }

.cert-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: -3px;
  width: 3px;
  height: 0;
  background: linear-gradient(180deg, var(--secondary-color), var(--accent-color));
  transition: height 0.3s ease;
}

.cert-card:hover::before {
  height: 100%;
}

.cert-card:hover {
  transform: translateY(-6px);
  box-shadow: 0 12px 30px rgba(37, 99, 235, 0.15);
  border-color: var(--secondary-color);
}

.cert-icon {
  font-size: 2.2rem;
  line-height: 1;
  flex-shrink: 0;
  transition: transform 0.3s ease;
}

.cert-card:hover .cert-icon {
  transform: scale(1.2) rotate(5deg);
}

.cert-body {
  flex: 1;
}

.cert-body h4 {
  color: var(--primary-color);
  font-size: 1.05rem;
  margin-bottom: 0.5rem;
  line-height: 1.4;
  font-weight: 600;
}

.cert-place {
  color: var(--text-light);
  font-size: 0.9rem;
  margin: 0;
}

.cert-date {
  color: var(--secondary-color);
  font-weight: 700;
  font-size: 0.8rem;
  white-space: nowrap;
  background: rgba(37, 99, 235, 0.1);
  padding: 0.4rem 0.8rem;
  border-radius: 6px;
  transition: all 0.3s ease;
}

.cert-card:hover .cert-date {
  background: linear-gradient(135deg, var(--secondary-color), var(--accent-color));
  color: var(--white);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .certs-layout {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .cert-card {
    padding: 1.2rem;
    gap: 1rem;
  }

  .cert-icon {
    font-size: 1.8rem;
  }

  .cert-body h4 {
    font-size: 0.95rem;
  }

  .cert-place {
    font-size: 0.85rem;
  }

  .cert-date {
    font-size: 0.7rem;
    padding: 0.3rem 0.5rem;
  }

  .column-title {
    font-size: 1.1rem;
    margin-bottom: 1.2rem;
  }

  .certifications h2 {
    margin-bottom: 1.8rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .certs-layout {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .cert-card {
    padding: 1.5rem;
  }

  .certifications h2 {
    margin-bottom: 2.5rem;
  }

  .column-title {
    margin-bottom: 1.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .certs-layout {
    grid-template-columns: 1fr 1fr;
    gap: 2.5rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .certs-layout {
    grid-template-columns: 1fr 1fr;
    gap: 3.5rem;
  }
}
</style>
