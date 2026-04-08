<template>
  <section id="about" class="about">
    <div class="container">
      <h2>{{ t('aboutTitle') }}</h2>
      <div class="about-content">
        <div class="about-text">
          <p>{{ t('aboutText1') }}</p>
          <p>{{ t('aboutText2') }}</p>
        </div>
        <div class="about-image">
          <div class="placeholder-image">
            <img 
              src="/IMG_20260215_145501_378-1.jpg" 
              alt="Photo de Sedrick Kouam"
              style="width: 260px; height: 260px; object-fit: cover; border-radius: 12px; box-shadow: 0 4px 16px rgba(30,64,175,0.15); border: 4px solid var(--white);"
            >
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'About',
  setup() {
    const t = inject('t')
    return { t }
  }
}
</script>

<style scoped>
.about {
  background-color: var(--bg-light);
}

.about h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.about-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}

.about-text p {
  font-size: 1.1rem;
  color: var(--text-light);
  margin-bottom: 1rem;
  line-height: 1.8;
}

.placeholder-image {
  background: var(--secondary-color);
  color: var(--white);
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem 0;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
  }
}
</style>
