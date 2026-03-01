# Site Redesign Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Replace the Hugo/Hermit theme with a clean, minimalist 3-page static site (home, cv, projects) inspired by hrescak.com.

**Architecture:** Pure HTML + one shared CSS file. No build system, no JavaScript, no dependencies beyond a Google Fonts CDN import. Three pages: `index.html`, `cv/index.html`, `projects/index.html`. Existing Hugo output files are replaced or removed.

**Tech Stack:** HTML5, CSS3, Google Fonts (Inter), GitHub Pages (CNAME already in place)

**Design Reference:** See `docs/plans/2026-02-28-site-redesign-design.md` for all content, color values, and layout decisions. Do not deviate from approved content without checking.

---

### Task 1: Create shared stylesheet

**Files:**
- Create: `style.css`
- Remove: `css/` directory (Hugo-generated, no longer needed)

**Step 1: Write `style.css`**

```css
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500&display=swap');

*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

:root {
  --bg: #fafaf9;
  --text: #1a1a1a;
  --muted: #6b7280;
  --link: #1a1a1a;
  --max-width: 640px;
}

html {
  font-family: 'Inter', sans-serif;
  font-size: 16px;
  background: var(--bg);
  color: var(--text);
  -webkit-font-smoothing: antialiased;
}

body {
  max-width: var(--max-width);
  margin: 0 auto;
  padding: 80px 24px 80px;
  line-height: 1.7;
}

/* Typography */
h1 {
  font-size: 1.1rem;
  font-weight: 500;
  margin-bottom: 32px;
  letter-spacing: -0.01em;
}

p {
  color: var(--text);
  margin-bottom: 16px;
}

p:last-of-type {
  margin-bottom: 0;
}

/* Links */
a {
  color: var(--link);
  text-decoration: none;
  border-bottom: 1px solid currentColor;
}

a:hover {
  color: var(--muted);
}

/* Nav links (home page inline links) */
.nav {
  margin-top: 40px;
  display: flex;
  flex-wrap: wrap;
  gap: 20px;
}

.nav a {
  color: var(--muted);
  font-size: 0.9rem;
  border-bottom: none;
}

.nav a:hover {
  color: var(--text);
}

/* Back link */
.back {
  display: inline-block;
  color: var(--muted);
  font-size: 0.9rem;
  margin-bottom: 56px;
  border-bottom: none;
}

.back:hover {
  color: var(--text);
}

/* Page title (cv, projects) */
.page-title {
  font-size: 1.1rem;
  font-weight: 500;
  margin-bottom: 48px;
  letter-spacing: -0.01em;
}

/* CV Timeline */
.timeline {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.timeline-entry {
  display: grid;
  grid-template-columns: 100px 1fr;
  gap: 24px;
  padding: 28px 0;
  border-top: 1px solid #e5e5e3;
}

.timeline-entry:last-child {
  border-bottom: 1px solid #e5e5e3;
}

.timeline-year {
  color: var(--muted);
  font-size: 0.85rem;
  padding-top: 2px;
  flex-shrink: 0;
}

.timeline-content strong {
  font-weight: 500;
  display: block;
  margin-bottom: 6px;
}

.timeline-content p {
  font-size: 0.95rem;
  color: #374151;
  margin-bottom: 0;
}

/* Projects */
.projects {
  display: flex;
  flex-direction: column;
  gap: 0;
}

.project-entry {
  padding: 28px 0;
  border-top: 1px solid #e5e5e3;
}

.project-entry:last-child {
  border-bottom: 1px solid #e5e5e3;
}

.project-name {
  font-weight: 500;
  font-size: 1rem;
  margin-bottom: 6px;
  display: block;
}

.project-name a {
  border-bottom: none;
}

.project-name a:hover {
  color: var(--muted);
}

.project-desc {
  font-size: 0.95rem;
  color: #374151;
  margin-bottom: 10px;
}

.project-tags {
  font-size: 0.8rem;
  color: var(--muted);
}

/* Mobile */
@media (max-width: 480px) {
  body {
    padding: 48px 20px 64px;
  }

  .timeline-entry {
    grid-template-columns: 1fr;
    gap: 4px;
  }

  .timeline-year {
    font-size: 0.8rem;
  }
}
```

**Step 2: Verify CSS file exists**

```bash
ls style.css
```
Expected: `style.css`

**Step 3: Commit**

```bash
git add style.css
git commit -m "feat: add shared minimalist stylesheet"
```

---

### Task 2: Create home page

**Files:**
- Modify: `index.html` (replace existing Hugo output entirely)

**Step 1: Write `index.html`**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Boyang Sa</title>
  <meta name="description" content="Data scientist working at the intersection of energy, transportation, climate, and policy.">
  <link rel="stylesheet" href="/style.css">
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
</head>
<body>
  <h1>Boyang Sa</h1>

  <p>I lead data science and analytical projects at the intersection
  of energy, transportation, climate, and policy. Currently
  Data Science Manager at the <a href="https://energycenter.org" target="_blank" rel="noopener">Center for Sustainable Energy</a>.</p>

  <p>I'm a parent of two — which is the hardest and best thing I do.
  I read fiction obsessively, follow baseball too closely, and build
  small tools to scratch my own itches or learn something new.</p>

  <nav class="nav">
    <a href="/cv">cv</a>
    <a href="/projects">projects</a>
    <a href="https://github.com/bobsa514" target="_blank" rel="noopener">github</a>
    <a href="https://www.linkedin.com/in/boyang-sa/" target="_blank" rel="noopener">linkedin</a>
    <a href="mailto:me@boyangsa.com">email</a>
  </nav>
</body>
</html>
```

**Step 2: Open in browser and verify**

Open `index.html` directly in a browser (file:// is fine for visual check). Confirm:
- Inter font loads
- Off-white background
- Text is readable, centered, max 640px
- Nav links at bottom in muted gray

**Step 3: Commit**

```bash
git add index.html
git commit -m "feat: add minimalist home page"
```

---

### Task 3: Create CV page

**Files:**
- Create: `cv/index.html`

**Step 1: Create directory and write `cv/index.html`**

```bash
mkdir -p cv
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>CV — Boyang Sa</title>
  <meta name="description" content="Career timeline of Boyang Sa, data scientist.">
  <link rel="stylesheet" href="/style.css">
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
</head>
<body>
  <a href="/" class="back">← Boyang Sa</a>

  <h1 class="page-title">CV</h1>

  <div class="timeline">

    <div class="timeline-entry">
      <span class="timeline-year">2022–</span>
      <div class="timeline-content">
        <strong>Center for Sustainable Energy</strong>
        <p>Started as a data scientist and now run the team. Most of
        the work lives at the edge of clean energy policy and real
        infrastructure — figuring out where chargers should go,
        whether programs are actually moving the needle, and making
        that legible to the people writing the checks. Built
        geospatial siting tools, carbon accounting models, causal
        inference studies. The work has touched a dozen states and
        a lot of federal dollars.</p>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2016–22</span>
      <div class="timeline-content">
        <strong>PhD, Urban Design and Planning — University of Washington</strong>
        <p>Six years thinking hard about who gets left out of the EV
        transition and why. The dissertation looked at charging
        infrastructure, policy, and equity — the gap between clean
        energy ambition and who it actually reaches.</p>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2016–20</span>
      <div class="timeline-content">
        <strong>World Bank (via UW)</strong>
        <p>Built a carbon accounting and climate risk model that ended
        up being adopted by 20+ municipalities across Tanzania, Uganda,
        Ethiopia, Indonesia, and Turkey. Watching something you built
        in a research lab inform real capital investment plans is a
        strange and good feeling.</p>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2016–19</span>
      <div class="timeline-content">
        <strong>Research Assistant — University of Washington</strong>
        <p>Helped stand up the UW Transportation Data Collaborative —
        a big-data platform bridging Microsoft, Lyft, Uber, Seattle
        DOT, and Sound Transit. Also helped write policy on autonomous
        vehicles before anyone really knew what that meant.</p>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2017–21</span>
      <div class="timeline-content">
        <strong>Instructor — University of Washington</strong>
        <p>Taught infrastructure planning, urban planning methods,
        and GIS at the master's level. Learned more from students
        than I expected.</p>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2013–15</span>
      <div class="timeline-content">
        <strong>MRP, City and Regional Planning — Cornell University</strong>
      </div>
    </div>

    <div class="timeline-entry">
      <span class="timeline-year">2009–13</span>
      <div class="timeline-content">
        <strong>BA, Geography (GIS) — University of Washington</strong>
      </div>
    </div>

  </div>
</body>
</html>
```

**Step 2: Verify in browser**

Open `cv/index.html`. Confirm:
- Timeline grid renders correctly (year left, content right)
- Horizontal rules between entries
- Back link works

**Step 3: Commit**

```bash
git add cv/index.html
git commit -m "feat: add CV timeline page"
```

---

### Task 4: Create projects page

**Files:**
- Create: `projects/index.html`

**Step 1: Create directory and write `projects/index.html`**

```bash
mkdir -p projects
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Projects — Boyang Sa</title>
  <meta name="description" content="Side projects by Boyang Sa.">
  <link rel="stylesheet" href="/style.css">
  <link rel="icon" type="image/png" sizes="32x32" href="/favicon-32x32.png">
  <link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon.png">
</head>
<body>
  <a href="/" class="back">← Boyang Sa</a>

  <h1 class="page-title">Projects</h1>

  <div class="projects">

    <div class="project-entry">
      <span class="project-name">
        <a href="https://github.com/bobsa514/mapviewer-gl" target="_blank" rel="noopener">mapviewer-gl ↗</a>
      </span>
      <p class="project-desc">A lightweight browser-based viewer for geospatial data — GeoJSON, CSV, H3. No server, no signup. Built to get more comfortable in the geospatial open-source world.</p>
      <span class="project-tags">TypeScript · React · deck.gl · Mapbox GL</span>
    </div>

    <div class="project-entry">
      <span class="project-name">
        <a href="https://github.com/bobsa514/ETFTrueHoldings" target="_blank" rel="noopener">ETFTrueHoldings ↗</a>
      </span>
      <p class="project-desc">X-ray your ETF portfolio to see what you actually own across funds. Scratched my own itch as someone who invests in a lot of overlapping ETFs.</p>
      <span class="project-tags">TypeScript · React · Recharts</span>
    </div>

    <div class="project-entry">
      <span class="project-name">
        <a href="https://github.com/bobsa514/TreeCarbonXray" target="_blank" rel="noopener">TreeCarbonXray ↗</a>
      </span>
      <p class="project-desc">Inventory trees and estimate lifetime carbon storage using USFS biomass data. Built partly to help my wife think through landscape design — she's a landscape architect.</p>
      <span class="project-tags">TypeScript · React · USFS i-Tree data</span>
    </div>

  </div>
</body>
</html>
```

**Step 2: Verify in browser**

Open `projects/index.html`. Confirm:
- Three project entries separated by horizontal rules
- GitHub links open correctly (↗ arrow is a nice touch)
- Tags render in muted gray

**Step 3: Commit**

```bash
git add projects/index.html
git commit -m "feat: add projects page"
```

---

### Task 5: Clean up Hugo artifacts

**Files:**
- Remove directories: `about/`, `posts/`, `tags/`, `css/`, `js/`
- Remove files: `index.xml`, `sitemap.xml`, `404.html`
- Keep: favicon files, `CNAME`, `site.webmanifest`, `browserconfig.xml`, `style.css`, `index.html`, `cv/`, `projects/`, `docs/`, `README.md`

**Step 1: Remove Hugo-generated directories and files**

```bash
rm -rf about/ posts/ tags/ css/ js/
rm -f index.xml sitemap.xml 404.html
```

**Step 2: Verify remaining structure**

```bash
ls
```

Expected output includes: `index.html`, `cv/`, `projects/`, `style.css`, `docs/`, `CNAME`, favicon files, `site.webmanifest`, `README.md`

**Step 3: Commit**

```bash
git add -A
git commit -m "chore: remove Hugo-generated artifacts"
```

---

### Task 6: Final check and push

**Step 1: Open each page in browser and verify**

- `index.html` — home loads, all nav links point to correct URLs
- `cv/index.html` — back link works, timeline renders, no layout breaks on mobile width (resize browser to 375px)
- `projects/index.html` — back link works, all GitHub links open, tags visible

**Step 2: Check CNAME is intact**

```bash
cat CNAME
```
Expected: `boyangsa.com` (or whatever the custom domain is)

**Step 3: Push to GitHub Pages**

```bash
git push origin main
```

**Step 4: Verify live site**

Visit `https://boyangsa.com` (or `https://bobsa514.github.io`) after a minute and confirm the live site matches local.
