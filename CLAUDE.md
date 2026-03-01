# boyangsa.com — Site Guide for AI Sessions

## What this site is

A minimalist personal site for Boyang Sa (Data Science Manager, Center for Sustainable Energy). Three pages, pure HTML+CSS, no build system, no JavaScript, no dependencies except a Google Fonts CDN import.

## File structure

```
index.html          → Home page
cv/index.html       → Career timeline
projects/index.html → Side projects
style.css           → Shared stylesheet (all styles live here)
CNAME               → Custom domain: boyangsa.com
docs/plans/         → Design docs and implementation plans
favicon-*.png       → Favicon files (don't touch)
site.webmanifest    → PWA manifest (don't touch)
```

## Design system

| Token | Value | Use |
|-------|-------|-----|
| `--bg` | `#fafaf9` | Page background |
| `--text` | `#1a1a1a` | Primary text |
| `--muted` | `#6b7280` | Secondary text, dates, tags |
| `--link` | `#1a1a1a` | Link color |
| `--max-width` | `640px` | Content max-width |
| Font | Inter (Google Fonts) | All text |

Rules:
- Never add JavaScript
- Never add a build step
- Never add a CSS framework
- Keep all styles in `style.css` — don't add `<style>` tags to HTML files
- Max content width is 640px, centered, with 80px top/bottom padding
- Mobile breakpoint at 480px (timeline stacks to single column)

## Page anatomy

### Home (`index.html`)
- `<h1>` — name only
- Two `<p>` paragraphs — professional bio, personal note
- `<nav class="nav">` — links: cv, projects, github, linkedin, email

### CV (`cv/index.html`)
- `<a class="back">` — back to home
- `<h1 class="page-title">` — "CV"
- `<div class="timeline">` containing `<div class="timeline-entry">` items
  - Each entry: `<span class="timeline-year">` + `<div class="timeline-content">`
  - `timeline-content` has a `<strong>` title and optional `<p>` description

### Projects (`projects/index.html`)
- `<a class="back">` — back to home
- `<h1 class="page-title">` — "Projects"
- `<div class="projects">` containing `<div class="project-entry">` items
  - Each entry: `<span class="project-name">` + `<p class="project-desc">` + `<span class="project-tags">`

## Common edits

### Add a new project

Copy this block into `projects/index.html` inside `<div class="projects">`:

```html
<div class="project-entry">
  <span class="project-name">
    <a href="https://github.com/bobsa514/REPO-NAME" target="_blank" rel="noopener">project-name ↗</a>
  </span>
  <p class="project-desc">One or two sentence description in plain language. Why it exists, what it does.</p>
  <span class="project-tags">Tech · Stack · Here</span>
</div>
```

### Add a CV timeline entry

Copy this block into `cv/index.html` inside `<div class="timeline">`, in chronological order (most recent first):

```html
<div class="timeline-entry">
  <span class="timeline-year">YYYY–YY</span>
  <div class="timeline-content">
    <strong>Role or Degree — Organization</strong>
    <p>Optional description. Keep it personal and narrative, not resume bullet points.</p>
  </div>
</div>
```

For entries with no description (e.g. degrees), omit the `<p>` entirely.

### Update home page bio

Edit the two `<p>` paragraphs in `index.html`. First paragraph is professional. Second is personal. Keep it short — 2 sentences max each.

### Update nav links

Edit the `<nav class="nav">` block in `index.html`. Current links: cv, projects, github, linkedin, email. Don't add more than 5-6 links — keep it minimal.

## Tone guide

- **CV descriptions:** Personal narrative, not resume bullets. First person implied. Tell a story — what you built, why it mattered, how it felt.
- **Project descriptions:** Plain language, one or two sentences. Why you built it, what it does. Don't over-engineer the description.
- **Home bio:** Honest, warm, specific. Mention real things (parent of two, fiction reader, baseball). Not a LinkedIn summary.

## Owner info

- **Name:** Boyang Sa, Ph.D.
- **Email:** me@boyangsa.com
- **GitHub:** https://github.com/bobsa514
- **LinkedIn:** https://www.linkedin.com/in/boyang-sa/
- **Employer:** Center for Sustainable Energy (https://energycenter.org)
- **Domain:** boyangsa.com (GitHub Pages, CNAME set)

## Deployment

This is a GitHub Pages site. Push to `main` and it deploys automatically. No build step.

```bash
git add -p          # stage specific changes
git commit -m "..."
git push origin main
```

The site is live at https://boyangsa.com within ~1 minute of pushing.

## What NOT to do

- Don't add a framework (React, Vue, Next.js, etc.)
- Don't add a CSS preprocessor (Sass, Less)
- Don't add a static site generator (Hugo, Jekyll, Eleventy)
- Don't add analytics (no tracking on this site)
- Don't add a contact form
- Don't add dark mode (intentional design decision)
- Don't add animations or transitions
- Don't create new pages without asking first
- Don't change the font (Inter is intentional)
- Don't change the color scheme without explicit instruction
