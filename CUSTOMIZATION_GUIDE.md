# Quick Customization Guide

## Common Updates You'll Want to Make

### 1. Update Your Resume PDF
**File**: `public/resume.pdf`
**Action**: Replace the placeholder file with your actual resume

```sh
# Replace with your resume
cp ~/Downloads/Myles_Lozano_Resume.pdf public/resume.pdf
```

### 2. Update Social Media Links
**File**: [src/data/profile.json](src/data/profile.json:9-13)

```json
"socials": {
  "github": "https://github.com/YOUR_USERNAME",
  "linkedin": "https://linkedin.com/in/YOUR_LINKEDIN",
  "twitter": "https://twitter.com/YOUR_HANDLE"
}
```

### 3. Add GitHub Links to Projects
**File**: [src/data/projects.json](src/data/projects.json)

Example for Hunter Radar:
```json
{
  "id": 1,
  "title": "Hunter Radar",
  "links": {
    "github": "https://github.com/tripoint/hunter-radar",
    "live": "https://hunterradar.com"  // if you have a demo
  }
}
```

### 4. Update Email Address
**Files to check**:
- [src/data/profile.json](src/data/profile.json:8) - Display email
- [src/pages/index.astro](src/pages/index.astro:502) - Contact form mailto

Make sure both match your preferred email.

### 5. Add More Projects
**File**: [src/data/projects.json](src/data/projects.json)

Add a new project:
```json
{
  "id": 4,
  "title": "Your New Project",
  "tagline": "Short description",
  "description": "Longer description of what you built and why",
  "role": "Your Role",
  "tech": ["Technology 1", "Technology 2", "Technology 3"],
  "links": {
    "github": "https://github.com/...",
    "live": "https://..."
  },
  "featured": true
}
```

### 6. Customize Skills
**File**: [src/pages/index.astro](src/pages/index.astro:183-243)

Find the skills arrays and modify:
```javascript
// Engineering & Design section
{['CAD (SolidWorks)', 'Product Design', 'Prototyping', ...].map((skill) => (
  // Add your skills here
))}
```

### 7. Add Awards (When Available)
**File**: [src/pages/index.astro](src/pages/index.astro:245-266)

1. Remove `hidden` class from the awards section
2. Replace placeholder content with real awards:

```html
<div>
  <h3 class="text-xl font-semibold text-gray-900 dark:text-white mb-2">
    Dean's Honor Roll
  </h3>
  <p class="text-gray-600 dark:text-gray-400 mb-3">
    Oklahoma State University • Fall 2024
  </p>
  <p class="text-gray-700 dark:text-gray-300 leading-relaxed">
    Recognized for academic excellence with a 4.0 GPA.
  </p>
</div>
```

### 8. Adjust Section Spacing
**File**: [src/pages/index.astro](src/pages/index.astro)

All sections use `py-32` for vertical padding. To change:
- More space: `py-40` or `py-48`
- Less space: `py-24` or `py-20`

Example:
```html
<!-- Before -->
<section id="about" class="py-32 px-4 ...">

<!-- After (more space) -->
<section id="about" class="py-40 px-4 ...">
```

### 9. Change Hero Text
**File**: [src/data/profile.json](src/data/profile.json)

```json
{
  "name": "Myles Lozano",
  "headline": "Update this to your preferred headline",
  "shortBio": "Update this short bio shown on the hero",
  "longBio": "Update this longer bio shown in About section..."
}
```

### 10. Customize Colors (Advanced)
**File**: [tailwind.config.mjs](tailwind.config.mjs)

To use a custom color palette instead of grayscale:

```javascript
theme: {
  extend: {
    colors: {
      primary: {
        50: '#...',
        100: '#...',
        // ... your color scale
      }
    }
  }
}
```

Then update components to use your colors instead of `gray-`.

## Quick Wins

### Remove Old Multi-Page Routes

If you only want the single-page experience:

```sh
rm src/pages/about.astro
rm src/pages/contact.astro
rm src/pages/projects.astro
rm src/pages/resume.astro

# Keep index.astro and 404.astro
```

### Update Site Title and Description

**File**: [astro.config.mjs](astro.config.mjs:8)

```javascript
site: 'https://myleslozano.com', // Your domain
```

**File**: [public/robots.txt](public/robots.txt:4)

```
Sitemap: https://myleslozano.com/sitemap-index.xml
```

### Add Custom Font (Optional)

**File**: [src/pages/index.astro](src/pages/index.astro) - Add to `<head>`:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**File**: [tailwind.config.mjs](tailwind.config.mjs)

```javascript
fontFamily: {
  sans: ['Inter', '-apple-system', 'BlinkMacSystemFont', ...],
},
```

## Testing Checklist

After customizations, verify:

- [ ] `npm run dev` - Site loads without errors
- [ ] `npm run build` - Build completes successfully
- [ ] Dark mode toggle works
- [ ] All nav links scroll smoothly to correct sections
- [ ] Active section highlighting works while scrolling
- [ ] Contact form opens email client
- [ ] Resume download link works
- [ ] All social links go to correct profiles
- [ ] Mobile menu opens and closes properly
- [ ] Site looks good on mobile (test in DevTools)

## Deployment

Once customizations are complete:

```sh
# Build for production
npm run build

# Deploy to Cloudflare Pages, Vercel, Netlify, etc.
# See README.md for detailed deployment instructions
```

## Need Help?

- Check [SINGLE_PAGE_REFACTOR.md](SINGLE_PAGE_REFACTOR.md) for architecture details
- Check [README.md](README.md) for deployment instructions
- Check [Astro docs](https://docs.astro.build)
- Check [Tailwind docs](https://tailwindcss.com)
