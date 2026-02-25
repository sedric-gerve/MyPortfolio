# My Professional Portfolio

A modern, professional portfolio website built with Vue 3 and Vite.

## Features

- **Responsive Design**: Works seamlessly on desktop, tablet, and mobile devices
- **Multiple Sections**: About, Skills, Experience, Projects, Blog, and Contact
- **Professional Styling**: Clean, minimalist design with smooth animations
- **Easy Customization**: Modify content directly in Vue components
- **Optimized Performance**: Built with Vite for fast development and production builds

## Project Structure

```
├── src/
│   ├── components/
│   │   ├── Navigation.vue    # Header navigation
│   │   ├── Hero.vue          # Hero section
│   │   ├── About.vue         # About me section
│   │   ├── Skills.vue        # Skills section
│   │   ├── Experience.vue    # Work experience timeline
│   │   ├── Projects.vue      # Project showcase
│   │   ├── Blog.vue          # Blog posts
│   │   ├── Contact.vue       # Contact form
│   │   └── Footer.vue        # Footer
│   ├── App.vue               # Root component
│   ├── main.js               # Application entry point
│   └── style.css             # Global styles
├── index.html                # HTML template
├── package.json              # Project dependencies
└── vite.config.js            # Vite configuration
```

## Getting Started

### Prerequisites

- Node.js 14+ installed
- npm or yarn package manager

### Installation

1. Navigate to the project directory:
```bash
cd portfolio
```

2. Install dependencies:
```bash
npm install
```

### Development

Start the development server with hot module replacement:

```bash
npm run dev
```

The application will open automatically at `http://localhost:5173`

### Building for Production

Create an optimized production build:

```bash
npm run build
```

Preview the production build:

```bash
npm run preview
```

## Customization

### Update Personal Information

Edit each component to add your own content:

- **Navigation.vue**: Update links and branding
- **Hero.vue**: Change name and subtitle
- **About.vue**: Write your bio and add your photo
- **Skills.vue**: Add your technical skills
- **Experience.vue**: List your work experience
- **Projects.vue**: Showcase your projects
- **Blog.vue**: Add your blog posts
- **Contact.vue**: Update contact information

### Colors and Styling

The color scheme is defined in `src/style.css` using CSS variables:

```css
:root {
  --primary-color: #2c3e50;
  --secondary-color: #3498db;
  --accent-color: #e74c3c;
  --text-dark: #2c3e50;
  --text-light: #7f8c8d;
  --bg-light: #ecf0f1;
  --white: #ffffff;
}
```

Modify these variables to change the overall color scheme.

## Deployment

### Recommended Platforms

- **Vercel**: Zero-config deployment with automatic builds
- **Netlify**: Git-based deployment with preview URLs
- **GitHub Pages**: Free hosting directly from your repository
- **AWS S3**: Cost-effective static site hosting

### Deploying to Vercel

1. Push your code to GitHub
2. Connect your repository to Vercel
3. Vercel will automatically build and deploy

## Technologies Used

- **Vue 3**: Progressive JavaScript framework
- **Vite**: Next-generation build tool
- **CSS3**: Modern styling with animations
- **HTML5**: Semantic markup

## Browser Support

- Chrome (latest)
- Firefox (latest)
- Safari (latest)
- Edge (latest)

## License

This project is open source and available under the MIT License.

## Support

For issues or questions, please create an issue in the repository.

---

**Happy coding!** 🚀
