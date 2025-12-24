# Quick Start Guide

## Run Locally (3 steps)

1. **Start the dev server**
   ```sh
   npm run dev
   ```

2. **Open your browser**
   - Go to `http://localhost:4321`

3. **Make it yours**
   - Edit `src/data/profile.json` with your info
   - Edit `src/data/projects.json` with your projects
   - Edit `src/pages/resume.astro` with your experience

## Deploy to Cloudflare Pages (Free)

### Option 1: Direct Upload (Fastest)

```sh
npm run build
```

Then go to [Cloudflare Pages](https://pages.cloudflare.com):
- Click "Upload assets"
- Drag the `dist` folder
- Done! Your site is live at `your-project.pages.dev`

### Option 2: Connect GitHub (Auto-deploys)

```sh
git init
git add .
git commit -m "Initial commit"
git push origin main
```

Then in Cloudflare:
- Connect your GitHub repo
- Build command: `npm run build`
- Build output: `dist`
- Click "Save and Deploy"

## Custom Domain Setup

1. **Point your domain to Cloudflare**
   - Change nameservers at your registrar
   - Use the nameservers Cloudflare provides

2. **Add custom domain in Cloudflare Pages**
   - Go to your project → Custom domains
   - Enter your domain (e.g., `loz.ano`)
   - Cloudflare automatically configures SSL

3. **Update site config**
   - Change `site:` in `astro.config.mjs` to your domain
   - Update sitemap URL in `public/robots.txt`

## Files to Customize

Priority files to update:

1. `src/data/profile.json` - Your personal info
2. `src/data/projects.json` - Your projects
3. `src/pages/resume.astro` - Your resume content
4. `public/resume.pdf` - Your resume PDF
5. `astro.config.mjs` - Your domain
6. `src/pages/contact.astro` - Your email (search for `mailto:`)

Optional files:
- `public/og-image.png` - Social media preview image
- `public/favicon.svg` - Browser tab icon

## Key Commands

```sh
npm run dev      # Start dev server
npm run build    # Build for production
npm run preview  # Preview production build
```

## Need Help?

- Full documentation: See [README.md](./README.md)
- Astro docs: [docs.astro.build](https://docs.astro.build)
- Cloudflare Pages: [developers.cloudflare.com/pages](https://developers.cloudflare.com/pages)
