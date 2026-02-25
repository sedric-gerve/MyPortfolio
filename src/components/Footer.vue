<template>
  <footer class="footer">
    <div class="container">
      <div class="footer-content">
        <p>&copy; 2026 Your Name. All rights reserved.</p>
        <div class="footer-links">
          <a href="#about">About</a>
          <a href="#projects">Projects</a>
          <a href="#blog">Blog</a>
          <a href="#contact">Contact</a>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background-color: var(--primary-color);
  color: var(--white);
  text-align: center;
  padding: 2rem 0;
}

.footer-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.footer-links {
  display: flex;
  gap: 2rem;
}

.footer-links a {
  color: rgba(255, 255, 255, 0.8);
  transition: color 0.3s;
}

.footer-links a:hover {
  color: var(--white);
}

@media (max-width: 768px) {
  .footer-content {
    flex-direction: column;
    gap: 1rem;
  }

  .footer-links {
    flex-wrap: wrap;
    justify-content: center;
  }
}
</style>
