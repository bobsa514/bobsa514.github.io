# Site Redesign Design Doc
_2026-02-28_

## Overview

Rebuild bobsa514.github.io as a clean, minimalist personal site inspired by hrescak.com. Replace the existing Hugo/Hermit theme with pure HTML + CSS — no build system, no JavaScript, no dependencies beyond a Google Fonts import.

## Style

- **Font:** Inter (Google Fonts, variable weight)
- **Background:** `#fafaf9` (warm off-white)
- **Text:** `#1a1a1a` (near-black), `#6b7280` for secondary/muted
- **Max content width:** 640px, centered
- **No dark mode** (keep it simple)
- **No decorative elements** — whitespace does the work
- Thin `<hr>` separators for CV timeline entries

## Structure

Three pages, shared CSS file:

```
index.html          → Home
cv/index.html       → CV
projects/index.html → Projects
style.css           → Shared styles
```

The existing Hugo output (posts/, about/, css/, js/, etc.) will be replaced/removed.

## Page Content

### Home (`/`)

```
Boyang Sa

I lead data science and analytical projects at the intersection
of energy, transportation, climate, and policy. Currently
Data Science Manager at the Center for Sustainable Energy.

I'm a parent of two — which is the hardest and best thing I do.
I read fiction obsessively, follow baseball too closely, and build
small tools to scratch my own itches or learn something new.

cv · projects · github · linkedin · email
```

Nav links: cv → /cv, projects → /projects, github → https://github.com/bobsa514, linkedin → https://www.linkedin.com/in/boyang-sa/, email → mailto:me@boyangsa.com

### CV (`/cv`)

Timeline layout: year left-aligned (muted), description right. Entries:

| Year | Entry |
|------|-------|
| 2022– | **Center for Sustainable Energy** — Started as a data scientist and now run the team. Most of the work lives at the edge of clean energy policy and real infrastructure — figuring out where chargers should go, whether programs are actually moving the needle, and making that legible to the people writing the checks. Built geospatial siting tools, carbon accounting models, causal inference studies. The work has touched a dozen states and a lot of federal dollars. |
| 2016–22 | **PhD, Urban Design and Planning, University of Washington** — Six years thinking hard about who gets left out of the EV transition and why. The dissertation looked at charging infrastructure, policy, and equity — the gap between clean energy ambition and who it actually reaches. |
| 2016–20 | **World Bank (via UW)** — Built a carbon accounting and climate risk model that ended up being adopted by 20+ municipalities across Tanzania, Uganda, Ethiopia, Indonesia, and Turkey. Watching something you built in a research lab inform real capital investment plans is a strange and good feeling. |
| 2016–19 | **Research Assistant, University of Washington** — Helped stand up the UW Transportation Data Collaborative — a big-data platform bridging Microsoft, Lyft, Uber, Seattle DOT, and Sound Transit. Also helped write policy on autonomous vehicles before anyone really knew what that meant. |
| 2017–21 | **Instructor, University of Washington** — Taught infrastructure planning, urban planning methods, and GIS at the master's level. Learned more from students than I expected. |
| 2013–15 | **MRP, City and Regional Planning, Cornell University** |
| 2009–13 | **BA, Geography (GIS), University of Washington** |

Back link to home at top.

### Projects (`/projects`)

Card list. Each entry: project name (linked to GitHub), one-line description, tech tags.

| Project | Description | Tags |
|---------|-------------|------|
| mapviewer-gl | A lightweight browser-based viewer for geospatial data — GeoJSON, CSV, H3. No server, no signup. | TypeScript · React · deck.gl · Mapbox GL |
| ETFTrueHoldings | X-ray your ETF portfolio to see what you actually own across funds. | TypeScript · React · Recharts |
| TreeCarbonXray | Inventory trees and estimate lifetime carbon storage using USFS biomass data. Built partly to help my wife think through landscape design. | TypeScript · React · USFS i-Tree |

Note: section is designed to grow — more side projects and CSE work projects will be added later.

Back link to home at top.

## Files to Create/Modify

- **Create:** `index.html` (replace existing)
- **Create:** `cv/index.html`
- **Create:** `projects/index.html`
- **Create:** `style.css` (single shared stylesheet)
- **Keep:** favicon files, CNAME, site.webmanifest
- **Remove/ignore:** Hugo-generated `about/`, `posts/`, `css/`, `js/`, `tags/`, `index.xml`, `sitemap.xml`

## Success Criteria

- Matches hrescak.com minimalist aesthetic
- All three pages render cleanly on mobile and desktop
- No build step required — edit HTML and push
- Links to GitHub, LinkedIn, and email all work
- CV reads as personal narrative, not a resume
