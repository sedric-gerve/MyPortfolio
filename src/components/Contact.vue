<template>
  <section id="contact" class="contact">
    <div class="container">
      <h2>{{ t('contactTitle') }}</h2>
      <p class="contact-intro">{{ t('contactIntro') }}</p>
      <div class="contact-content">
        <form @submit.prevent="submitForm" class="contact-form">
          <div class="form-group">
            <input
              v-model="form.name"
              type="text"
              :placeholder="t('yourName')"
              required
              class="form-input"
            />
          </div>
          <div class="form-group">
            <input
              v-model="form.email"
              type="email"
              :placeholder="t('yourEmail')"
              required
              class="form-input"
            />
          </div>
          <div class="form-group">
            <input
              v-model="form.subject"
              type="text"
              :placeholder="t('subject')"
              required
              class="form-input"
            />
          </div>
          <div class="form-group">
            <textarea
              v-model="form.message"
              :placeholder="t('yourMessage')"
              rows="6"
              required
              class="form-input"
            ></textarea>
          </div>
          <button type="submit" class="submit-btn">{{ t('sendMessage') }}</button>
        </form>
        <div class="contact-info">
          <div class="info-item">
            <div class="info-icon">📧</div>
            <div>
              <h4>{{ t('email') }}</h4>
              <p><a :href="`mailto:${contactDetails.email}`">{{ contactDetails.email }}</a></p>
            </div>
          </div>
          <div class="info-item">
            <div class="info-icon">📍</div>
            <div>
              <h4>{{ t('location') }}</h4>
              <p>{{ t('locationValue') }}</p>
            </div>
          </div>
          <div class="info-item">
            <div class="info-icon">🔗</div>
            <div>
              <h4>{{ t('social') }}</h4>
              <div class="social-links">
                <a v-for="link in contactDetails.social" :key="link.url" :href="link.url" target="_blank" rel="noopener noreferrer">{{ link.name }}</a>
              </div>
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
  name: 'Contact',
  setup() {
    const t = inject('t')
    return {
      t,
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      },
      contactDetails: {
        email: 'kouamsedrick@gmail.com',
        social: [
          {
            name: 'LinkedIn',
            url: 'https://www.linkedin.com/in/sedrick-kouam-9237a8241'
          },
          {
            name: 'GitHub',
            url: 'https://github.com/sedric-gerve'
          }
        ]
      }
    }
  },
  data() {
    return {
      form: {
        name: '',
        email: '',
        subject: '',
        message: ''
      }
    }
  },
  methods: {
    submitForm() {
      // Handle form submission
      alert(this.t('thankYouMessage'))
      this.form = { name: '', email: '', subject: '', message: '' }
    }
  }
}
</script>

<style scoped>
.contact {
  background-color: var(--white);
}

.contact h2 {
  text-align: center;
  margin-bottom: 0.5rem;
}

.contact-intro {
  text-align: center;
  color: var(--text-light);
  margin-bottom: 2rem;
  font-size: 1.1rem;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  margin-top: 2rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
}

.form-input {
  padding: 0.8rem;
  border: 1px solid var(--bg-light);
  border-radius: 5px;
  font-family: inherit;
  font-size: 1rem;
  transition: border-color 0.3s;
}

.form-input:focus {
  outline: none;
  border-color: var(--secondary-color);
}

.submit-btn {
  background-color: var(--secondary-color);
  color: var(--white);
  padding: 1rem;
  border-radius: 5px;
  font-size: 1rem;
  font-weight: 600;
  transition: background-color 0.3s;
}

.submit-btn:hover {
  background-color: var(--accent-color);
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 2rem;
}

.info-item {
  display: flex;
  gap: 1rem;
}

.info-icon {
  font-size: 2rem;
}

.info-item h4 {
  color: var(--primary-color);
  margin-bottom: 0.3rem;
}

.info-item p {
  color: var(--text-light);
}

.info-item p a {
  color: var(--secondary-color);
  font-weight: 500;
  text-decoration: none;
}

.info-item p a:hover {
  color: var(--accent-color);
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.social-links a {
  color: var(--secondary-color);
  font-weight: 500;
}

.social-links a:hover {
  color: var(--accent-color);
}

@media (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
  }
}
</style>
