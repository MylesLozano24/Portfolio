# Portfolio Website

A modern, minimal portfolio website built with Astro and Tailwind CSS. Features dark mode, responsive design, and excellent Lighthouse scores.

## Features

- Modern minimal design with clean typography and spacious layout
- Dark mode toggle with localStorage persistence and system preference detection
- Fully responsive and mobile-first
- Accessible with ARIA labels, focus states, and skip-to-content link
- SEO optimized with meta tags, Open Graph, and Twitter cards
- Automatic sitemap generation
- Fast static site generation
- Project showcase with filtering
- Contact form with mailto fallback
- Downloadable resume

## Project Structure

```
lozano-portfolio/
├── public/
│   ├── favicon.svg
│   ├── og-image.png          # Replace with your Open Graph image
│   ├── resume.pdf            # Replace with your actual resume
│   └── robots.txt
├── src/
│   ├── components/
│   │   ├── Footer.astro
│   │   ├── Navigation.astro
│   │   ├── ProjectCard.astro
│   │   └── SEO.astro
│   ├── data/
│   │   ├── profile.json      # Your personal information
│   │   └── projects.json     # Your projects
│   ├── layouts/
│   │   └── Layout.astro
│   └── pages/
│       ├── 404.astro
│       ├── about.astro
│       ├── contact.astro
│       ├── index.astro
│       ├── projects.astro
│       └── resume.astro
├── astro.config.mjs
├── tailwind.config.mjs
└── package.json
```

## Getting Started

### 1. Install Dependencies

```sh
npm install
```

### 2. Customize Your Content

Edit the data files to personalize your portfolio:

**src/data/profile.json**
```json
{
  "name": "Your Name",
  "headline": "Your Title",
  "location": "Your Location",
  "email": "your.email@example.com",
  "socials": {
    "github": "https://github.com/yourusername",
    "linkedin": "https://linkedin.com/in/yourusername",
    "twitter": "https://twitter.com/yourusername"
  },
  "shortBio": "Your short bio...",
  "longBio": "Your longer bio..."
}
```

**src/data/projects.json**
- Update with your actual projects
- Set `"featured": true` for projects to appear on the home page (max 3)

### 3. Update Configuration

**astro.config.mjs**
- Change `site: 'https://yourdomain.com'` to your actual domain

**src/pages/contact.astro**
- Update the email address in the form submit handler (line with `mailto:`)

### 4. Add Your Files

- Replace `public/og-image.png` with your Open Graph image (1200x630px recommended)
- Replace `public/resume.pdf` with your actual resume PDF
- Optionally, replace `public/favicon.svg` with your own favicon

### 5. Update Resume Content

Edit `src/pages/resume.astro` with your actual:
- Work experience
- Education
- Skills
- Awards and recognition

## Development Commands

| Command | Action |
| :--- | :--- |
| `npm install` | Install dependencies |
| `npm run dev` | Start dev server at `localhost:4321` |
| `npm run build` | Build production site to `./dist/` |
| `npm run preview` | Preview production build locally |

## Deployment

### Deploy to Cloudflare Pages (Free)

1. **Build your site**
   ```sh
   npm run build
   ```

2. **Create a Cloudflare account**
   - Go to [dash.cloudflare.com](https://dash.cloudflare.com/sign-up)
   - Sign up for a free account

3. **Deploy via Git (Recommended)**

   a. Push your code to GitHub:
   ```sh
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/yourusername/your-repo.git
   git push -u origin main
   ```

   b. In Cloudflare Dashboard:
   - Go to Workers & Pages
   - Click "Create application"
   - Select "Pages" tab
   - Click "Connect to Git"
   - Authorize GitHub and select your repository
   - Configure build settings:
     - Framework preset: `Astro`
     - Build command: `npm run build`
     - Build output directory: `dist`
   - Click "Save and Deploy"

4. **Deploy via Direct Upload (Alternative)**

   a. Build your site:
   ```sh
   npm run build
   ```

   b. In Cloudflare Dashboard:
   - Go to Workers & Pages
   - Click "Create application"
   - Select "Pages" tab
   - Click "Upload assets"
   - Drag and drop the `dist` folder or select it
   - Enter a project name
   - Click "Deploy site"

5. **Your site is live!**
   - Cloudflare will provide a URL like `your-project.pages.dev`
   - Every push to your main branch will automatically deploy

### Connect a Custom Domain to Cloudflare Pages

1. **Add your domain to Cloudflare**

   a. In Cloudflare Dashboard:
   - Click "Add a site"
   - Enter your domain (e.g., `loz.ano`)
   - Select the Free plan
   - Click "Continue"

   b. Update nameservers at your domain registrar:
   - Cloudflare will show you 2 nameservers
   - Go to your domain registrar (where you bought the domain)
   - Find DNS/Nameserver settings
   - Replace existing nameservers with Cloudflare's nameservers
   - Wait for DNS propagation (can take up to 24 hours, usually much faster)

2. **Connect domain to your Pages project**

   a. In Cloudflare Dashboard:
   - Go to Workers & Pages
   - Click on your portfolio project
   - Go to "Custom domains" tab
   - Click "Set up a custom domain"

   b. Add your domain:
   - Enter your domain: `loz.ano`
   - Click "Continue"
   - Cloudflare will automatically configure DNS
   - Click "Activate domain"

   c. (Optional) Add www subdomain:
   - Click "Set up a custom domain" again
   - Enter `www.loz.ano`
   - Click "Continue" and "Activate domain"

3. **Enable HTTPS**
   - Cloudflare automatically provisions SSL certificates
   - Your site will be available at `https://loz.ano` within a few minutes

4. **Update your site configuration**
   - In `astro.config.mjs`, update:
     ```js
     site: 'https://loz.ano',
     ```
   - In `public/robots.txt`, update:
     ```
     Sitemap: https://loz.ano/sitemap-index.xml
     ```
   - Commit and push changes (or re-deploy)

### Other Deployment Options

- **Vercel**: Connect GitHub repo, auto-detects Astro, zero config
- **Netlify**: Drag and drop `dist` folder or connect Git
- **GitHub Pages**: Use GitHub Actions with Astro's official workflow
- **Any static host**: Upload the `dist` folder contents

## Customization

### Colors

The site uses Tailwind's default color palette with a grayscale theme. To customize:

1. Edit `tailwind.config.mjs` to add your color palette
2. Update component classes to use your colors
3. Adjust dark mode colors in component files

### Fonts

The site uses system fonts for performance. To add custom fonts:

1. Add font files to `public/fonts/` or use a service like Google Fonts
2. Update `tailwind.config.mjs` to include your font
3. Add font loading in `src/layouts/Layout.astro`

### Animations

Subtle animations are included via Tailwind. Customize in `tailwind.config.mjs`:

```js
animation: {
  'fade-in': 'fadeIn 0.6s ease-in-out',
  'slide-up': 'slideUp 0.6s ease-out',
}
```

## Performance

This site is optimized for performance:

- Static site generation (no JavaScript required for content)
- Minimal dependencies
- Optimized images
- No external font loading
- Efficient CSS with Tailwind's purge
- Lighthouse scores typically 95+ across all metrics

## Browser Support

- Modern browsers (Chrome, Firefox, Safari, Edge)
- Mobile browsers (iOS Safari, Chrome Mobile)
- Graceful degradation for older browsers

## License

This project is open source and available under the MIT License.

## Support

For questions or issues:
- Check [Astro documentation](https://docs.astro.build)
- Review [Tailwind CSS docs](https://tailwindcss.com)
- Open an issue on GitHub
