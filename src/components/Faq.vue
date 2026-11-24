<template>
  <section id="faq" class="faq">
    <div class="container">
      <span class="eyebrow">{{ t('faqEyebrow') }}</span>
      <div class="section-head">
        <h2>{{ t('faqTitle') }}</h2>
        <span class="rule"></span>
      </div>
      <p class="faq-intro">{{ t('faqIntro') }}</p>

      <div class="faq-list">
        <div
          v-for="(item, i) in items"
          :key="item.id"
          class="faq-item"
          :class="{ open: openIndex === i }"
        >
          <button
            class="faq-question"
            :aria-expanded="openIndex === i"
            @click="toggle(i)"
          >
            <span>{{ t(item.question) }}</span>
            <span class="faq-icon" aria-hidden="true">{{ openIndex === i ? '−' : '+' }}</span>
          </button>
          <div class="faq-answer-wrap">
            <div class="faq-answer-inner">
              <p class="faq-answer">{{ t(item.answer) }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject, ref } from 'vue'

export default {
  name: 'Faq',
  setup() {
    const t = inject('t')
    const openIndex = ref(0)

    const items = [
      { id: 1, question: 'faq1Q', answer: 'faq1A' },
      { id: 2, question: 'faq2Q', answer: 'faq2A' },
      { id: 3, question: 'faq3Q', answer: 'faq3A' },
      { id: 4, question: 'faq4Q', answer: 'faq4A' },
      { id: 5, question: 'faq5Q', answer: 'faq5A' },
      { id: 6, question: 'faq6Q', answer: 'faq6A' }
    ]

    const toggle = (i) => {
      openIndex.value = openIndex.value === i ? -1 : i
    }

    return { t, items, openIndex, toggle }
  }
}
</script>

<style scoped>
.faq {
  background: var(--primary-color);
  position: relative;
}

.faq::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(249, 115, 22, 0.4), transparent);
  opacity: 0.3;
}

.eyebrow {
  display: block;
  color: var(--accent-color);
  font-size: 0.78rem;
  font-weight: 700;
  letter-spacing: 0.12em;
  text-transform: uppercase;
  margin-bottom: 1rem;
}

.faq-intro {
  color: var(--text-on-dark-muted);
  font-size: 1.05rem;
  max-width: 560px;
  margin-top: -2.5rem;
  margin-bottom: 3rem;
}

.faq-list {
  max-width: 760px;
  border-top: 1px solid var(--line-on-ink);
}

.faq-item {
  border-bottom: 1px solid var(--line-on-ink);
}

.faq-question {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: space-between;
  gap: 1.5rem;
  background: transparent;
  padding: 1.5rem 0;
  text-align: left;
  font-family: var(--font-display);
  font-size: 1.1rem;
  font-weight: 600;
  color: var(--white);
}

.faq-icon {
  flex-shrink: 0;
  width: 28px;
  height: 28px;
  display: flex;
  align-items: center;
  justify-content: center;
  border: 1px solid var(--accent-color);
  border-radius: 3px;
  color: var(--accent-color);
  font-size: 1rem;
  font-weight: 700;
}

.faq-answer-wrap {
  display: grid;
  grid-template-rows: 0fr;
  transition: grid-template-rows 0.3s ease;
}

.faq-item.open .faq-answer-wrap {
  grid-template-rows: 1fr;
}

.faq-answer-inner {
  overflow: hidden;
}

.faq-answer {
  color: var(--text-on-dark-muted);
  line-height: 1.7;
  font-size: 0.98rem;
  max-width: 620px;
  padding-bottom: 1.6rem;
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .faq-intro {
    margin-top: 0;
    margin-bottom: 2rem;
  }

  .faq-question {
    font-size: 0.98rem;
    padding: 1.2rem 0;
    gap: 1rem;
  }

  .faq-icon {
    width: 24px;
    height: 24px;
    font-size: 0.9rem;
  }

  .faq-answer {
    font-size: 0.92rem;
  }
}
</style>
