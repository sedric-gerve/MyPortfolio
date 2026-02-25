# GitHub Copilot Instructions for Portfolio Project

This file contains workspace-specific instructions for working with this Vue.js portfolio project.

## Project Overview

- **Type**: Vue 3 + Vite portfolio website
- **Purpose**: Professional portfolio with multiple sections (About, Skills, Experience, Projects, Blog, Contact)
- **Technology Stack**: Vue 3, Vite, CSS3
- **Node Version**: 14+

## Key Commands

- `npm install` - Install dependencies
- `npm run dev` - Start development server (http://localhost:5173)
- `npm run build` - Build for production
- `npm run preview` - Preview production build

## Project Structure

```
src/
├── components/       - Vue components for each section
├── App.vue          - Main app component
├── main.js          - Entry point
└── style.css        - Global styles
```

## Important Files to Edit

When customizing the portfolio:

1. **src/components/About.vue** - Bio and about information
2. **src/components/Hero.vue** - Main title and subtitle
3. **src/components/Skills.vue** - Technical skills (update the skills array in data())
4. **src/components/Experience.vue** - Work history (update jobs array in data())
5. **src/components/Projects.vue** - Portfolio projects (update projects array in data())
6. **src/components/Blog.vue** - Blog posts (update posts array in data())
7. **src/components/Contact.vue** - Contact information and social links
8. **src/style.css** - Colors and global styling (CSS variables at the root)

## Common Tasks

### Add a new skill
Edit `src/components/Skills.vue` and add an object to the `skills` array.

### Add project to portfolio
Edit `src/components/Projects.vue` and add an object to the `projects` array.

### Change color scheme
Edit CSS variables in `src/style.css` (--primary-color, --secondary-color, etc.)

### Add a blog post
Edit `src/components/Blog.vue` and add an object to the `posts` array.

## Deployment

The built files go to `dist/` folder. Deploy to any static hosting:
- Vercel (recommended)
- Netlify
- GitHub Pages
- AWS S3

## Design Features

- Fully responsive (mobile, tablet, desktop)
- Smooth scroll behavior
- Hover animations and transitions
- Professional color scheme
- Accessibility-friendly

## Next Steps

1. Run `npm install` to install dependencies
2. Run `npm run dev` to start development server
3. Customize all components with your information
4. Replace placeholder content (images, text, links)
5. Deploy to your preferred platform
