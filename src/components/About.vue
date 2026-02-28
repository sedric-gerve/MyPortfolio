<template>
  <section id="about" class="about">
    <div class="container">
      <h2>About Me</h2>
      <div class="about-content">
        <div class="about-text">
          <p>
            I'm a passionate Full Stack Web Developer with 6+ years of experience building scalable web applications. 
            I specialize in the TALL stack (Tailwind CSS, Alpine.js, Livewire, and Laravel) to create robust, 
            efficient solutions. I combine clean code practices with exceptional user experiences to deliver 
            high-quality web applications that solve real-world business problems.
          </p>
          <p>
            Throughout my career, I've worked on diverse projects ranging from SaaS platforms to enterprise solutions. 
            My expertise includes MySQL database design, containerization with Docker, version control with Git/GitHub, 
            and full-stack development. I'm passionate about writing maintainable code and constantly learning new technologies 
            to stay ahead in the rapidly evolving tech landscape.
          </p>
        </div>
        <div class="about-image">
          <div class="placeholder-image"> <img src="/IMG_20260215_145501_378-1.jpg" alt="Your picture">  </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'About'
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
  aspect-ratio: 1;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.2rem;
  font-weight: 600;
}

@media (max-width: 768px) {
  .about-content {
    grid-template-columns: 1fr;
  }
}
</style>
