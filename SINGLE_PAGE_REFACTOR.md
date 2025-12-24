# Single Page Portfolio - Refactor Complete

## Overview

Your portfolio has been successfully refactored into a modern, single-page scrolling site with smooth navigation and active section highlighting. Everything is now on one page at `index.astro`.

## What Changed

### Architecture
- **Before**: Multi-page site with separate routes (/about, /projects, /resume, /contact)
- **After**: Single-page application with smooth scrolling sections (#home, #about, #projects, #experience, #skills, #resume, #contact)

### Navigation
- **Sticky top nav** with smooth scroll to section anchors
- **Active section highlighting** using IntersectionObserver
- **Mobile-friendly** hamburger menu
- **Dark mode toggle** persists via localStorage
- **Smooth scroll behavior** throughout the site

### Content Updates

#### Profile Data ([src/data/profile.json](src/data/profile.json))
- Name: Myles Lozano
- Headline: Mechanical and aerospace engineering student, builder, and problem solver
- School: Oklahoma State University
- Major: Dual Major: Aerospace Engineering & Mechanical Engineering
- Class Standing: Sophomore (Junior by credit hours)
- Location: Stillwater, Oklahoma
- Email: myles.lozano@okstate.edu

#### Projects ([src/data/projects.json](src/data/projects.json))
1. **Hunter Radar** - TriPoint Innovations flagship product
2. **NPDC Engineering Projects** - OSU product development work
3. **SRC New Product Development** - Manufacturing innovation work

#### Experience ([src/data/experience.json](src/data/experience.json))
1. Springfield Remanufacturing Company (SRC) - New Product Development Intern
2. OSU New Product Development Center (NPDC) - Mechanical Engineering Intern
3. GE Aerospace - Engineering Intern (Summer 2026)
4. TriPoint Innovations LLC - Cofounder & Managing Member

## Sections Breakdown

### 1. Home (#home)
- Full-screen hero section
- Name, headline, school
- CTA buttons: "View Projects" and "Get in Touch"
- Centered, spacious layout

### 2. About (#about)
- Long bio with multiple paragraphs
- Education details (school, major, class standing)
- Contact information (location, email)

### 3. Projects (#projects)
- All 3 engineering projects displayed
- Project cards with hover effects
- Shows role, tech stack, and descriptions

### 4. Experience (#experience)
- Timeline-style layout with visual timeline
- All 4 positions with descriptions and achievements
- Period, location, and current status indicators

### 5. Skills (#skills)
- Four skill categories:
  - Engineering & Design
  - Technical & Software
  - Aerospace & Mechanical
  - Leadership & Business
- Tag-style skill badges

### 6. Awards (#awards)
- Currently hidden (no data yet)
- Ready to be revealed when you have awards to add
- Remove `hidden` class from section to show

### 7. Resume (#resume)
- Prominent download button
- Links to `/resume.pdf` (replace with actual resume)

### 8. Contact (#contact)
- Contact form with mailto fallback
- Direct email and location display
- Social media links (GitHub, LinkedIn, Twitter)

## Key Features

### Smooth Scrolling
- Clicking nav links smoothly scrolls to sections
- Offset accounts for sticky navigation height
- Works on all anchor links including footer "Back to top"

### Active Section Highlighting
- IntersectionObserver tracks visible section
- Nav link highlights automatically as you scroll
- Active state: darker text + background color

### Dark Mode
- Toggle button in nav (desktop + mobile)
- Persists preference in localStorage
- Respects system preference on first visit
- Smooth color transitions

### Accessibility
- Skip to content link (focus to reveal)
- Proper heading hierarchy (H1 > H2 > H3)
- ARIA labels on interactive elements
- Focus states with ring utilities
- Semantic HTML5 sections

### Mobile Responsive
- Mobile-first design
- Hamburger menu on mobile
- Responsive grid layouts
- Touch-friendly tap targets

## File Structure

```
src/
├── components/
│   ├── ProjectCard.astro          # Reused from before
│   ├── SEO.astro                  # Reused from before
│   ├── SinglePageNav.astro        # NEW - Sticky nav with active highlighting
│   └── SinglePageFooter.astro     # NEW - Footer with back to top
├── data/
│   ├── profile.json               # UPDATED - Myles's real info
│   ├── projects.json              # UPDATED - 3 engineering projects
│   └── experience.json            # NEW - All work experience
└── pages/
    ├── index.astro                # COMPLETELY REFACTORED - Single page app
    ├── about.astro                # Still exists (old multi-page version)
    ├── contact.astro              # Still exists (old multi-page version)
    ├── projects.astro             # Still exists (old multi-page version)
    ├── resume.astro               # Still exists (old multi-page version)
    └── 404.astro                  # Still exists
```

## Old Pages

The old multi-page routes still exist:
- `/about`
- `/projects`
- `/resume`
- `/contact`
- `/404`

These can be **safely deleted** if you only want the single-page experience, OR kept as fallback pages. The sitemap will still include them.

To remove old pages:
```sh
rm src/pages/about.astro
rm src/pages/contact.astro
rm src/pages/projects.astro
rm src/pages/resume.astro
```

## Commands

```sh
# Development
npm run dev

# Production build (tested ✓)
npm run build

# Preview production build
npm run preview
```

## Next Steps

### Essential Updates

1. **Replace resume PDF**
   - Upload your actual resume to `public/resume.pdf`
   - Current file is a placeholder

2. **Update social links**
   - Edit [src/data/profile.json](src/data/profile.json:9-13)
   - Replace GitHub, LinkedIn, Twitter URLs with your actual profiles

3. **Add real project links**
   - Edit [src/data/projects.json](src/data/projects.json)
   - Add GitHub repos or live demo links

### Optional Enhancements

4. **Add awards section**
   - Edit [src/pages/index.astro](src/pages/index.astro:245-266)
   - Remove `hidden` class from awards section
   - Add your actual awards data

5. **Customize skills**
   - Edit skills arrays in [src/pages/index.astro](src/pages/index.astro:195-240)
   - Add/remove skills as needed

6. **Adjust spacing**
   - All sections use `py-32` (128px vertical padding)
   - Modify to taste for more/less whitespace

7. **Update email in contact form**
   - Form currently sends to `myles.lozano@okstate.edu`
   - Verify this is correct or update in [src/pages/index.astro](src/pages/index.astro:502)

## Design Characteristics

- **Premium minimal vibe** - Lots of whitespace, crisp typography
- **System fonts** - Fast load, native feel
- **Grayscale palette** - Professional, timeless
- **Subtle animations** - fade-in, slide-up on page load
- **Smooth interactions** - Hover states, transitions
- **Dark mode** - Full support with persistence

## Performance

- **Static generation** - All HTML pre-rendered
- **Minimal JavaScript** - Only for dark mode, mobile menu, and smooth scroll
- **No runtime dependencies** - Pure static site
- **Expected Lighthouse scores**: 95-100 across all metrics

## Browser Support

- Chrome/Edge/Firefox/Safari latest
- Mobile Safari iOS 12+
- Smooth scroll supported in all modern browsers

---

**Your single-page portfolio is ready!** Run `npm run dev` to see it in action.
