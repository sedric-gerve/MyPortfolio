<template>
  <section id="blog" class="blog">
    <div class="container">
      <h2>Latest Blog Posts</h2>
      <div class="blog-grid">
        <article v-for="post in posts" :key="post.id" class="blog-card">
          <div class="blog-date">{{ post.date }}</div>
          <h3>{{ post.title }}</h3>
          <p class="blog-excerpt">{{ post.excerpt }}</p>
          <div class="blog-tags">
            <span v-for="tag in post.tags" :key="tag" class="blog-tag">{{ tag }}</span>
          </div>
          <a href="#" class="read-more">Read More →</a>
        </article>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Blog',
  data() {
    return {
      posts: [
        {
          id: 1,
          title: 'Getting Started with Vue 3 Composition API',
          excerpt: 'Learn how to use the new Composition API in Vue 3 for more flexible component logic organization.',
          date: 'Feb 20, 2026',
          tags: ['Vue.js', 'JavaScript']
        },
        {
          id: 2,
          title: 'Best Practices for React Performance',
          excerpt: 'Explore techniques to optimize your React applications and improve rendering performance.',
          date: 'Feb 15, 2026',
          tags: ['React', 'Performance']
        },
        {
          id: 3,
          title: 'Understanding Async/Await in JavaScript',
          excerpt: 'Deep dive into asynchronous JavaScript with async/await and how to handle promises effectively.',
          date: 'Feb 10, 2026',
          tags: ['JavaScript', 'Async']
        }
      ]
    }
  }
}
</script>

<style scoped>
.blog {
  background-color: var(--bg-light);
}

.blog h2 {
  text-align: center;
  margin-bottom: 3rem;
}

.blog-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
}

.blog-card {
  background: var(--white);
  padding: 2rem;
  border-radius: 10px;
  transition: all 0.3s;
  display: flex;
  flex-direction: column;
}

.blog-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
}

.blog-date {
  color: var(--secondary-color);
  font-size: 0.9rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}

.blog-card h3 {
  color: var(--primary-color);
  margin-bottom: 0.8rem;
  line-height: 1.4;
}

.blog-excerpt {
  color: var(--text-light);
  margin-bottom: 1rem;
  flex-grow: 1;
  line-height: 1.6;
}

.blog-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.blog-tag {
  background: var(--secondary-color);
  color: var(--white);
  padding: 0.25rem 0.7rem;
  border-radius: 15px;
  font-size: 0.8rem;
}

.read-more {
  color: var(--secondary-color);
  font-weight: 600;
  transition: color 0.3s;
}

.read-more:hover {
  color: var(--accent-color);
}
</style>
