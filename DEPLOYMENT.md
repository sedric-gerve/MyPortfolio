# Deployment Guide

Your portfolio is ready to deploy! Choose your preferred hosting platform below.

## Option 1: GitHub Pages (Free, Recommended)

### Prerequisites
- GitHub account
- Git installed on your machine
- Your code ready in this directory

### Steps

1. **Create a GitHub Repository**
   - Go to [github.com/new](https://github.com/new)
   - Name it: `portfolio` or anything you prefer
   - Click "Create repository"

2. **Add Remote and Push Code**
   ```bash
   git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
   git branch -M main
   git push -u origin main
   ```
   Replace `YOUR_USERNAME` and `YOUR_REPO_NAME` with your actual GitHub username and repository name.

3. **Enable GitHub Pages**
   - Go to your repository on GitHub
   - Click **Settings** → **Pages**
   - Under "Source", select **Deploy from a branch**
   - Select **main** branch and **/root** folder
   - Click **Save**

4. **Wait for Deployment**
   - GitHub will build and deploy automatically
   - Check the **Actions** tab to see the build status
   - Your portfolio will be live at: `https://YOUR_USERNAME.github.io/YOUR_REPO_NAME/`

### Auto-Deploy on Push
Every time you push changes to the main branch, GitHub Pages will automatically rebuild and deploy your portfolio. The GitHub Actions workflow (`.github/workflows/deploy.yml`) handles this automatically.

---

## Option 2: Railway (Free Tier Available, Easy Deployment)

### Prerequisites
- GitHub account
- Your portfolio pushed to GitHub (see Option 1 steps 1-2)
- Railway account at [railway.app](https://railway.app)

### Steps

1. **Sign Up on Railway**
   - Go to [railway.app](https://railway.app)
   - Sign up with GitHub (easiest option)

2. **Create New Project**
   - Click "New Project"
   - Select "Deploy from GitHub repo"

3. **Connect Your Repository**
   - Select your portfolio repository
   - Authorize Railway to access your GitHub account
   - Select the repository and click Deploy

4. **Configure Railway**
   - Railway auto-detects Node.js project
   - It will use the Dockerfile and railway.json we created
   - Configure environment variables if needed (usually none for static sites)

5. **Wait for Deployment**
   - Railway builds and deploys automatically
   - Check the project dashboard for build logs
   - Your portfolio will be live at Railway's assigned domain
   - You can add a custom domain in Railway settings

### Auto-Deploy on Push
Every push to your main branch on GitHub will trigger an automatic rebuild and deployment on Railway.

---

## Manual Deployment (Any Hosting)

If you want to use another hosting service (Netlify, Vercel, AWS S3, etc.), follow these steps:

1. **Build the Production Files**
   ```bash
   npm run build
   ```
   This creates a `dist/` folder with your complete portfolio.

2. **Deploy the `dist` Folder**
   - Upload the entire `dist/` folder to your hosting service
   - Set the public root to the `dist` folder
   - Make sure index.html is accessible at the root

3. **Example for Netlify**
   - Drag and drop the `dist` folder into Netlify
   - Your site will be live immediately

---

## Local Development

To test locally before deployment:

```bash
npm install
npm run dev
```

Visit `http://localhost:5173` in your browser.

---

## Troubleshooting

### Build Fails
- Make sure Node.js 14+ is installed
- Run `npm install --legacy-peer-deps`
- Check for syntax errors in your Vue components

### GitHub Pages Shows 404
- Ensure you set the source branch to `main` in GitHub Pages settings
- Check that your repository is public
- Verify the build completed successfully in the Actions tab

### Railway Deployment Not Updating
- Check the build logs in Railway dashboard
- Ensure your git push completed successfully
- Force railway to rebuild if needed

---

## Environment-Specific Configuration

For custom domains or specific hosting requirements, edit these files:

- **`vite.config.js`** - Vite build configuration
- **`Dockerfile`** - Docker image for containerization
- **`railway.json`** - Railway-specific settings
- **`.github/workflows/deploy.yml`** - GitHub Actions configuration

---

## Support

If you encounter deployment issues:

1. Check the build logs in your hosting service's dashboard
2. Verify all files are committed to git
3. Ensure Node.js dependencies are installed
4. Check that `npm run build` works locally

For framework-specific issues, refer to:
- [Vue 3 Documentation](https://vuejs.org/)
- [Vite Documentation](https://vitejs.dev/)
- [Railway Documentation](https://docs.railway.app/)
- [GitHub Pages Documentation](https://docs.github.com/en/pages)
