<template>
  <section id="contact" class="contact">
    <div class="container">
      <div class="section-head">
        <h2>{{ t('contactTitle') }}</h2>
        <span class="rule"></span>
      </div>
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
            <div class="info-icon">📱</div>
            <div>
              <h4>{{ t('phone') }}</h4>
              <p><a :href="`tel:${contactDetails.phone.replace(/\s/g, '')}`">{{ contactDetails.phone }}</a></p>
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
        phone: '(+237) 651382384',
        social: [
          {
            name: 'LinkedIn',
            url: 'https://www.linkedin.com/in/sedric-kouam'
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
  background: var(--primary-color);
  position: relative;
}

.contact::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.contact-intro {
  color: var(--text-on-dark-muted);
  margin-top: -2.5rem;
  margin-bottom: 3.5rem;
  font-size: 1.05rem;
  max-width: 560px;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-input {
  padding: 0.9rem 1rem;
  border: 1px solid var(--line-on-paper);
  border-radius: 4px;
  font-family: inherit;
  font-size: 1rem;
  transition: border-color 0.2s ease;
  background-color: var(--paper);
  color: var(--ink-on-paper);
}

.form-input::placeholder {
  color: var(--text-lighter);
}

.form-input:focus {
  outline: none;
  border-color: var(--accent-color);
}

.submit-btn {
  background: var(--accent-color);
  color: var(--white);
  padding: 1rem;
  border-radius: 4px;
  font-size: 1rem;
  font-weight: 600;
  transition: background 0.2s ease;
  cursor: pointer;
  margin-top: 0.5rem;
}

.submit-btn:hover {
  background: #EA580C;
}

.contact-info {
  display: flex;
  flex-direction: column;
  border-top: 1px solid var(--line-on-ink);
}

.info-item {
  display: flex;
  gap: 1.3rem;
  padding: 1.5rem 0;
  border-bottom: 1px solid var(--line-on-ink);
}

.info-icon {
  font-size: 1.6rem;
  flex-shrink: 0;
  line-height: 1.4;
}

.info-item h4 {
  color: var(--text-on-dark-muted);
  margin-bottom: 0.3rem;
  font-size: 0.85rem;
  font-weight: 500;
}

.info-item p {
  color: var(--white);
  font-size: 1rem;
  margin: 0;
}

.info-item p a {
  color: var(--white);
  font-weight: 500;
  transition: color 0.2s ease;
}

.info-item p a:hover {
  color: var(--accent-color);
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  margin-top: 0.2rem;
}

.social-links a {
  color: var(--white);
  font-weight: 500;
  width: fit-content;
}

.social-links a:hover {
  color: var(--accent-color);
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .contact-intro {
    margin-top: 0;
    margin-bottom: 2rem;
    font-size: 0.95rem;
  }

  .contact-form {
    gap: 1.2rem;
  }

  .form-input {
    padding: 0.8rem;
    font-size: 0.95rem;
  }

  .submit-btn {
    padding: 1rem;
    font-size: 0.95rem;
  }

  .info-item {
    padding: 1.1rem 0;
    gap: 1rem;
  }

  .info-icon {
    font-size: 1.4rem;
  }

  .info-item p {
    font-size: 0.9rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .contact-intro {
    margin-bottom: 2rem;
    font-size: 1rem;
  }

  .contact-form {
    gap: 1.5rem;
  }
}

/* Large Tablets (769px - 1024px) */
@media (min-width: 769px) and (max-width: 1024px) {
  .contact-content {
    grid-template-columns: 1fr 1fr;
    gap: 3rem;
  }
}

/* Large Screens (1025px+) */
@media (min-width: 1025px) {
  .contact-content {
    gap: 4rem;
  }
}
</style>
