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
  background-color: var(--bg-light);
}

.certifications h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.certs-layout {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
}

.column-title {
  color: var(--secondary-color);
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
  padding-bottom: 0.5rem;
  border-bottom: 2px solid var(--secondary-color);
}

.card-list {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.cert-card {
  background: var(--white);
  border-radius: 10px;
  padding: 1.2rem 1.4rem;
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.05);
  transition: transform 0.3s, box-shadow 0.3s;
}

.cert-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.cert-icon {
  font-size: 1.8rem;
  line-height: 1;
}

.cert-body {
  flex: 1;
}

.cert-body h4 {
  color: var(--primary-color);
  font-size: 1rem;
  margin-bottom: 0.3rem;
  line-height: 1.4;
}

.cert-place {
  color: var(--text-light);
  font-size: 0.9rem;
}

.cert-date {
  color: var(--secondary-color);
  font-weight: 600;
  font-size: 0.8rem;
  white-space: nowrap;
}

@media (max-width: 768px) {
  .certs-layout {
    grid-template-columns: 1fr;
    gap: 2.5rem;
  }
}
</style>
