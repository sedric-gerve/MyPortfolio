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
  background: linear-gradient(180deg, var(--bg-lighter) 0%, var(--white) 100%);
  position: relative;
}

.contact::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, var(--secondary-color), transparent);
  opacity: 0.3;
}

.contact h2 {
  text-align: center;
  margin-bottom: 1rem;
  animation: fadeInUp 0.7s ease-out;
}

.contact-intro {
  text-align: center;
  color: var(--text-light);
  margin-bottom: 3.5rem;
  font-size: 1.1rem;
  max-width: 800px;
  margin-left: auto;
  margin-right: auto;
  animation: fadeInUp 0.7s ease-out 0.1s both;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  margin-top: 3rem;
}

.contact-form {
  display: flex;
  flex-direction: column;
  gap: 1.8rem;
  animation: slideInLeft 0.8s ease-out;
}

.form-group {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.form-input {
  padding: 1rem;
  border: 1.5px solid var(--bg-light);
  border-radius: 10px;
  font-family: inherit;
  font-size: 1rem;
  transition: all 0.3s ease;
  background-color: var(--white);
  color: var(--text-dark);
}

.form-input::placeholder {
  color: var(--text-lighter);
}

.form-input:focus {
  outline: none;
  border-color: var(--secondary-color);
  box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
  background-color: rgba(37, 99, 235, 0.02);
}

.form-input:hover {
  border-color: var(--secondary-color);
}

.submit-btn {
  background: linear-gradient(135deg, var(--secondary-color) 0%, var(--accent-color) 100%);
  color: var(--white);
  padding: 1.2rem;
  border-radius: 10px;
  font-size: 1.05rem;
  font-weight: 600;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(37, 99, 235, 0.3);
  cursor: pointer;
  margin-top: 0.5rem;
}

.submit-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.4);
}

.submit-btn:active {
  transform: translateY(0);
}

.contact-info {
  display: flex;
  flex-direction: column;
  gap: 2.5rem;
  animation: slideInRight 0.8s ease-out;
}

.info-item {
  display: flex;
  gap: 1.5rem;
  padding: 1.8rem;
  background: var(--white);
  border-radius: 12px;
  border: 1px solid var(--bg-light);
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.08);
}

.info-item:hover {
  transform: translateY(-2px);
  box-shadow: 0 8px 25px rgba(37, 99, 235, 0.12);
  border-color: var(--secondary-color);
}

.info-icon {
  font-size: 2.2rem;
  flex-shrink: 0;
}

.info-item h4 {
  color: var(--primary-color);
  margin-bottom: 0.5rem;
  font-size: 1.1rem;
}

.info-item p {
  color: var(--text-light);
  font-size: 0.95rem;
  margin: 0;
}

.info-item p a {
  color: var(--secondary-color);
  font-weight: 600;
  text-decoration: none;
  transition: color 0.3s ease;
}

.info-item p a:hover {
  color: var(--accent-color);
}

.social-links {
  display: flex;
  flex-direction: column;
  gap: 0.8rem;
  margin-top: 0.5rem;
}

.social-links a {
  color: var(--secondary-color);
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s ease;
  display: inline-flex;
  align-items: center;
  gap: 0.6rem;
  width: fit-content;
}

.social-links a::before {
  content: '→';
  opacity: 0;
  transition: all 0.3s ease;
}

.social-links a:hover {
  color: var(--accent-color);
  padding-left: 0.4rem;
}

.social-links a:hover::before {
  opacity: 1;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .contact h2 {
    margin-bottom: 0.5rem;
  }

  .contact-intro {
    margin-bottom: 1.5rem;
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
    padding: 1.2rem;
    gap: 1rem;
  }

  .info-icon {
    font-size: 1.8rem;
  }

  .info-item h4 {
    font-size: 1rem;
  }

  .info-item p {
    font-size: 0.9rem;
  }

  .social-links {
    gap: 0.5rem;
  }

  .contact-info {
    gap: 1rem;
  }
}

/* Tablets (481px - 768px) */
@media (min-width: 481px) and (max-width: 768px) {
  .contact-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .contact h2 {
    margin-bottom: 0.5rem;
  }

  .contact-intro {
    margin-bottom: 2rem;
    font-size: 1rem;
  }

  .contact-form {
    gap: 1.5rem;
  }

  .info-item {
    padding: 1.5rem;
  }

  .contact-info {
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
