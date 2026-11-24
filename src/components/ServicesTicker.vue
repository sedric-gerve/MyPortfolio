<template>
  <div class="ticker" aria-hidden="true">
    <div class="ticker-track">
      <div class="ticker-group">
        <span v-for="name in serviceNames" :key="name" class="ticker-item">
          {{ t(name) }}
          <span class="ticker-dot">&#10022;</span>
        </span>
      </div>
      <div class="ticker-group">
        <span v-for="name in serviceNames" :key="name + '-dup'" class="ticker-item">
          {{ t(name) }}
          <span class="ticker-dot">&#10022;</span>
        </span>
      </div>
    </div>
  </div>
</template>

<script>
import { inject } from 'vue'

export default {
  name: 'ServicesTicker',
  setup() {
    const t = inject('t')
    const serviceNames = ['svcWebName', 'svcAgentsName', 'svcRagName', 'svcSeoName', 'svcDeployName']
    return { t, serviceNames }
  }
}
</script>

<style scoped>
.ticker {
  background: var(--accent-color);
  overflow: hidden;
  border-top: 1px solid rgba(0, 0, 0, 0.15);
  border-bottom: 1px solid rgba(0, 0, 0, 0.15);
}

.ticker-track {
  display: flex;
  width: max-content;
  animation: ticker-scroll 26s linear infinite;
}

.ticker:hover .ticker-track {
  animation-play-state: paused;
}

.ticker-group {
  display: flex;
  align-items: center;
  flex-shrink: 0;
}

.ticker-item {
  display: inline-flex;
  align-items: center;
  gap: 1.1rem;
  font-family: var(--font-display);
  font-weight: 600;
  font-size: 1rem;
  letter-spacing: 0.03em;
  color: var(--primary-color);
  white-space: nowrap;
  padding: 0.9rem 1.1rem;
}

.ticker-dot {
  color: rgba(13, 27, 51, 0.5);
  font-size: 0.8rem;
}

@keyframes ticker-scroll {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-50%);
  }
}

@media (prefers-reduced-motion: reduce) {
  .ticker-track {
    animation: none;
  }
}

/* Mobile Phones (320px - 480px) */
@media (max-width: 480px) {
  .ticker-item {
    font-size: 0.85rem;
    gap: 0.8rem;
    padding: 0.7rem 0.8rem;
  }
}
</style>
