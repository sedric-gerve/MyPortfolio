# Vercel Deployment Guide

Your portfolio is ready to deploy on Vercel! Follow these simple steps:

## Prerequisites
- GitHub account (your code must be on GitHub)
- Vercel account at [vercel.com](https://vercel.com)
- Your portfolio already pushed to GitHub

## Deployment Steps

### Step 1: Sign Up on Vercel
1. Go to [vercel.com](https://vercel.com)
2. Click **Sign Up**
3. Choose **Continue with GitHub**
4. Authorize Vercel to access your GitHub account

### Step 2: Import Your Repository
1. Click **New Project** on Vercel dashboard
2. Select **Import Git Repository**
3. Find and select your `portfolio` repository from GitHub
4. Click **Import**

### Step 3: Configure Project
Vercel will auto-detect this is a Vue 3 + Vite project. Settings should be:
- **Framework Preset**: Vue.js
- **Build Command**: `npm run build`
- **Output Directory**: `dist`
- **Install Command**: `npm install --legacy-peer-deps`

Everything is pre-configured in `vercel.json`, so you can just click **Deploy**!

### Step 4: Deploy
1. Click the **Deploy** button
2. Vercel will build and deploy your portfolio
3. Wait for the deployment to complete (usually 30-60 seconds)
4. Your portfolio will be live at: `https://YOUR_PROJECT_NAME.vercel.app`

## Your Live Portfolio URL
After deployment, you'll get a URL like:
```
https://portfolio-seven-phi.vercel.app
(exact URL will be different based on your project name)
```

You can copy this URL and share it with anyone!

## Custom Domain (Optional)
To use your own domain:
1. Go to your project settings on Vercel
2. Click **Domains**
3. Add your custom domain
4. Follow the DNS configuration instructions
5. Your portfolio will be accessible at your custom domain

## Auto-Deployment
Every time you push changes to your GitHub repository's main branch, Vercel will automatically:
1. Detect the changes
2. Build your portfolio
3. Deploy the new version live

No additional steps needed - it's automatic! 🚀

## Environment Variables (if needed)
If you add environment variables later:
1. Go to **Settings** → **Environment Variables** on Vercel
2. Add your variables
3. Click **Save**
4. Vercel will auto-redeploy with the new environment

## Monitoring Deployments
- **Deployments Tab**: See all deployment history
- **Logs**: View build logs and error messages
- **Analytics**: Monitor traffic and performance
- **Preview URLs**: Test changes before going live

## Rollback (if needed)
If something goes wrong:
1. Go to **Deployments** tab
2. Find the previous working deployment
3. Click **Promote to Production**
4. Done! Your previous version is live again

## Troubleshooting

### Build Fails
- Check the build logs in Vercel dashboard
- Ensure all files are committed to GitHub
- Try running `npm run build` locally to verify it works

### Portfolio Not Updating
- Wait a few seconds for the deployment to complete
- Hard refresh your browser (Ctrl+Shift+R)
- Check the Deployments tab to ensure the build succeeded

### Custom Domain Not Working
- Verify DNS settings are configured correctly
- Allow 24-48 hours for DNS to propagate
- Check Vercel's domain dashboard for status

## Useful Vercel Links
- [Vercel Dashboard](https://vercel.com/dashboard)
- [Vercel Documentation](https://vercel.com/docs)
- [Vercel Support](https://vercel.com/support)

---

**That's it!** Your portfolio is now deployed on Vercel and will automatically update whenever you push changes to GitHub. 🎉
