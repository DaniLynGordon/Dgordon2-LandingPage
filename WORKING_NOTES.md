# Working Notes — Dani Gordon's Landing Page

> **Internal document — not for public audiences.**
> This file is for developer and AI assistant reference only. Update it at the end of every working session before closing.

---

## How to Use This File (For AI Assistants)

1. Read this entire file before suggesting any changes or writing any code.
2. Read `README.md` for the public-facing project description, tech stack, and deployment setup.
3. Do not change the folder structure or file naming conventions without discussing it first.
4. Follow all conventions listed in the **Conventions** section exactly — do not introduce new patterns.
5. Do not suggest any approach listed in **What Was Tried and Rejected**.
6. Ask a clarifying question before making any large structural change (e.g., adding JavaScript, changing the CSS architecture, or reorganizing sections).
7. This project was built with AI assistance (Claude). Refactor conservatively — prefer targeted edits over rewrites.

---

## Current State

**Last Updated:** March 31, 2026

The site is a complete, fully responsive static landing page. All planned sections are built and populated with real content. It is deployed to Azure Static Web Apps and auto-deploys from the `main` branch on GitHub. No JavaScript is used anywhere.

### What Is Working
- [x] Sticky navigation bar with anchor links to all six sections
- [x] Hero section with circular headshot, name, tagline, and location
- [x] About Me bio section with first-person copy
- [x] Education section with University of Iowa, GPA 3.9/4.0, Dean's List, and Leadership & Involvement
- [x] Skills section with three color-coded pill-badge groups (Technical Tools, Analytical Skills, Business & Professional Skills)
- [x] Work Experience section — Archway Pet (Marketing Lead + Business Operations & Analytics Intern), Mauro Provisions, Hudson Burnham
- [x] Projects section — three cards in a 3-column desktop grid (Data4Good, SQL Analytics, NBA Python)
- [x] Contact section with LinkedIn, email, and GitHub icon badges
- [x] Fully responsive layout (320px – desktop)
- [x] Azure Static Web Apps CI/CD deployment via GitHub Actions
- [x] `README.md` with all 16 required sections
- [x] `STANDARDS.md` and `PRD.md` present in repo root

### What Is Partially Built
- [ ] **Color contrast audit** — palette was chosen visually; a formal WCAG AA contrast ratio check with an automated tool has not been run
- [ ] **Cross-browser visual testing** — tested in Chrome only; Safari and Firefox have not been visually verified

### What Is Not Started
- [ ] Dark mode support
- [ ] Contact / inquiry form
- [ ] Analytics / visitor tracking (Google Analytics or similar)
- [ ] Individual project detail pages

---

## Current Task

The initial build is complete and the page is live. The most recent session addressed several user-requested content and layout changes: correcting Archway Pet employment dates, moving the Education section above Skills, reformatting the project grid from 2-column to 3-column, and expanding the Skills section with a third category (Business & Professional Skills).

**The very next step is:** Run a cross-browser visual check in Safari and Firefox to confirm the layout, fonts, and skill pill badges render correctly.

---

## Architecture and Tech Stack

| Technology | Version | Why It Was Chosen |
|---|---|---|
| HTML5 | Current | Required by STANDARDS.md; semantic elements ensure accessibility and logical structure |
| CSS3 | Current | Required by STANDARDS.md; vanilla CSS only — no frameworks allowed |
| Google Fonts — Playfair Display | Latest | Chosen for a professional-yet-feminine heading style per user's design direction |
| Google Fonts — Inter | Latest | Clean, highly legible sans-serif for body copy; pairs well with Playfair Display |
| CSS Custom Properties | Native | Centralizes the color palette and spacing tokens so edits propagate everywhere |
| CSS Grid | Native | Powers the 3-column project grid and responsive collapse |
| CSS Flexbox | Native | Powers the nav, skill tags, contact badges, and role-title rows |
| Azure Static Web Apps | Current | Already configured in the repo from the original GitHub import; free tier, auto-deploys from `main` |
| GitHub Actions | Current | CI/CD workflow file was present in the repo from day one; no additional setup required |

---

## Project Structure Notes

```
Dgordon2-LandingPage/
├── index.html                   # Single-page site — all content lives here
├── css/
│   └── stylesheet.css           # All styles; organized top-to-bottom by section
├── Images/
│   └── Dani_Gordon.png          # Headshot — referenced as Images/Dani_Gordon.png
├── .github/
│   └── workflows/
│       └── azure-static-web-apps-calm-beach-0842aef0f.yml
├── attached_assets/             # Uploaded prompt/instruction files — not part of the site
├── PRD.md                       # Product requirements — source of truth for content
├── STANDARDS.md                 # Technical and design rules — must be followed on every edit
├── README.md                    # Public-facing project documentation
├── WORKING_NOTES.md             # This file
├── replit.md                    # Replit environment notes
└── .replit                      # Replit workflow config (serves site on port 5000)
```

**Non-obvious decisions:**
- The `Images/` folder uses a capital `I` — this matches the original repo import. Do not rename it without updating the `src` attribute in `index.html` at the same time, or the headshot will break.
- There is no `js/` folder and no `scripts.js` file. STANDARDS.md prohibits JavaScript. Do not create one.
- `Dani_Gordon_Resume_2026.pdf` exists in the repo root but is intentionally **not linked anywhere** on the site, per STANDARDS.md ("Do not link to or embed my resume anywhere on the site").
- `attached_assets/` contains uploaded prompt instruction files used during the build session. It is not part of the deployed site.

**Files that must not be changed without discussion:**
- `.github/workflows/azure-static-web-apps-calm-beach-0842aef0f.yml` — modifying this could break the Azure deployment pipeline
- `Images/Dani_Gordon.png` — the only headshot; do not rename, move, or replace without confirming the new path in `index.html`

---

## Data / Database

This project has no database, no backend, and no persistent data of any kind. It is a fully static site. All content is hard-coded in `index.html`.

---

## Conventions

### Naming Conventions
- HTML file: `index.html` (lowercase, singular)
- CSS file: `css/stylesheet.css` (lowercase)
- Image folder: `Images/` (capital I — matches existing repo; do not change)
- Image file: `Dani_Gordon.png` (underscores, title case)
- CSS class names: lowercase hyphenated (BEM-lite) — e.g., `.exp-card`, `.role-name`, `.tag-accent`
- CSS custom properties: `--color-*` for palette, `--font-*` for typography, `--radius-*` for border radii, `--shadow-*` for box shadows

### Code Style Rules
- No inline `style=""` attributes anywhere in HTML — all styles must be in `css/stylesheet.css`
- No `<style>` tags in `index.html`
- No JavaScript — not even a `<script>` tag
- All external links use `target="_blank" rel="noopener noreferrer"`
- SVG icons are inlined in HTML (not separate files or external URLs)
- Section order in `index.html` matches the nav order: Hero → About → Education → Skills → Experience → Projects → Contact → Footer
- CSS is organized in the same top-to-bottom section order as the HTML

### Heading Hierarchy
- `<h1>`: Dani L. Gordon (hero only — one per page)
- `<h2>`: Section headings (About Me, Education, Skills, etc.)
- `<h3>`: Card/subsection headings (employer names, project names, role names, degree names)

### Git Commit Message Style
Short imperative sentences, present tense, no period. Examples:
- `Fix Archway Pet employment dates`
- `Add Business & Professional Skills group`
- `Move Education section above Skills`

---

## Decisions and Tradeoffs

- **Vanilla CSS only, no framework:** Required by STANDARDS.md. Keeps the codebase simple, beginner-friendly, and free of build tools. Do not suggest adding Tailwind, Bootstrap, or any other CSS framework.
- **No JavaScript:** Required by STANDARDS.md. The site is intentionally static and read-only. Do not suggest adding JS for animations, form handling, or interactivity.
- **Playfair Display + Inter font pairing:** Chosen to meet the user's request for a design that is "professional and a little girly." Playfair Display provides an elegant, serif heading style; Inter is neutral and highly legible for body copy.
- **Dusty rose (#b5547a) accent color:** Chosen to satisfy the "professional and a little girly" design direction while maintaining sufficient contrast against the near-white background for WCAG compliance.
- **3-column project grid:** Changed from 2-column after the user noted the original 2+1 layout looked uneven with three cards. Three equal columns resolve this on desktop; the grid collapses to 2 on tablet and 1 on mobile.
- **Education placed above Skills:** User explicitly requested this section order. The current order (About → Education → Skills → Experience → Projects → Contact) must be maintained.
- **Resume not linked on site:** STANDARDS.md explicitly prohibits linking to or embedding the resume. The PDF file in the repo root is for the author's own reference only.
- **SVG icons inlined:** Contact section icons (LinkedIn, email, GitHub) are inlined SVG paths rather than an external icon library. This avoids adding a dependency and keeps the page self-contained.
- **Headshot referenced as `Images/Dani_Gordon.png`:** The capital `I` in `Images/` matches the folder name in the original repo import. Changing it would require renaming both the folder and the HTML reference simultaneously.

---

## What Was Tried and Rejected

- **2-column project grid:** Implemented initially but rejected by the user because three cards in a 2+1 layout looked uneven. Replaced with a 3-column grid. Do not suggest reverting to 2-column.
- **Education section at the bottom (after Projects):** Was the original placement. The user requested it be moved to directly below About Me. Do not suggest moving it back.
- **`@import` in CSS for Google Fonts:** Was present in the initial stylesheet alongside the `<link>` tag in HTML, causing duplicate font loading. The `@import` was removed; fonts are now loaded via `<link>` in `index.html` only.
- **Separate `js/scripts.js` file:** The STANDARDS.md folder structure template included a `js/` folder, but no JavaScript is used and no such file was created. Do not suggest creating one.

---

## Known Issues and Workarounds

- **Image folder uses capital `Images/`:** Non-standard casing (convention is lowercase `images/`). No workaround — the folder name and the `src` attribute in `index.html` match each other. If you rename the folder, you must also update the `src` attribute or the headshot will break on case-sensitive servers (Linux/Azure).
- **No formal contrast ratio audit:** Colors were chosen visually and checked by eye. A `--color-text` of `#1a1a2e` on `--color-bg` of `#fdf6f9` should pass WCAG AA (estimated ratio ~14:1), but the tertiary tag palette (`#5c3d6b` on `#f0eaf4`) has not been formally verified. Do not remove these color values without re-checking contrast.
- **Sticky nav overlap on anchor scroll:** The sticky header (60px tall) can partially obscure section headings when anchor links are clicked. A CSS `scroll-margin-top` has not been applied to section elements. This is a known minor issue with no workaround currently in place.

---

## Browser / Environment Compatibility

| Browser | Status |
|---|---|
| Chrome (desktop) | Tested — renders correctly |
| Edge (desktop) | Expected to work — same Chromium engine as Chrome |
| Firefox (desktop) | Not yet verified |
| Safari (desktop) | Not yet verified |
| Chrome (mobile) | Responsive breakpoints confirmed via screenshot |
| Safari (iOS) | Not yet verified |

**`backdrop-filter` note:** The sticky nav uses `backdrop-filter: blur(8px)` for a frosted-glass effect. This is supported in all modern browsers but may render without the blur effect in very old Firefox versions — the nav background color remains visible as a fallback.

---

## Open Questions

- Should a `scroll-margin-top` offset be added to section elements to prevent the sticky nav from overlapping headings on anchor scroll?
- Should Google Analytics (or a privacy-friendly alternative like Plausible) be added to measure the success metrics in the PRD?
- Should the `Images/` folder be renamed to `images/` (lowercase) for web convention consistency, and both the folder and `index.html` updated at the same time?
- If a contact form is added in the future, which service should handle form submission — Formspree, Netlify Forms, or something else?
- Is the `Dani_Gordon_Resume_2026.pdf` in the repo root intentional, or should it be removed to avoid it being publicly accessible via the deployed URL?

---

## Session Log

### 2026-03-31
- Set up Replit environment; configured Python HTTP server workflow on port 5000; configured Azure Static Web Apps deployment target
- Built complete `index.html` with all seven sections (Hero, About, Education, Skills, Experience, Projects, Contact) using real content from resume and PRD
- Built complete `css/stylesheet.css` with full design system: blush/rose + navy palette, Playfair Display + Inter typography, skill pill badges, responsive project grid, sticky nav, contact icon badges
- Added third Business & Professional Skills group (Communication, Public Speaking, Leadership, etc.)
- Corrected Archway Pet dates: Intern June–August 2025, promoted to Marketing Lead August 2025–Present
- Moved Education section above Skills per user request
- Changed project grid from 2-column to 3-column for visual balance
- Generated `README.md` with all 16 required sections
- Generated `WORKING_NOTES.md` (this file)
- **Left incomplete:** Cross-browser testing (Safari, Firefox); formal WCAG contrast ratio audit; `scroll-margin-top` fix for sticky nav anchor scroll
- **Decisions made:** 3-column project grid, dusty rose accent, Playfair Display heading font, no JavaScript, no resume link on site
- **Next step when resuming:** Visually verify layout in Safari and Firefox; consider adding `scroll-margin-top` to section elements

---

## Useful References

- [HTML5 Semantic Elements — MDN](https://developer.mozilla.org/en-US/docs/Glossary/Semantics#semantics_in_html)
- [CSS Custom Properties — MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Using_CSS_custom_properties)
- [CSS Grid Layout — MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_grid_layout)
- [WCAG 2.2 Quick Reference](https://www.w3.org/WAI/WCAG22/quickref/)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/) — use this to verify color contrast ratios
- [Google Fonts — Playfair Display](https://fonts.google.com/specimen/Playfair+Display)
- [Google Fonts — Inter](https://fonts.google.com/specimen/Inter)
- [Azure Static Web Apps Documentation](https://learn.microsoft.com/en-us/azure/static-web-apps/)
- [Shields.io Badge Generator](https://shields.io/)
- **AI Assistance:** Page structure, CSS architecture, and content organization were generated using Claude (Anthropic) based on the author's `PRD.md`, `STANDARDS.md`, and resume. All content was reviewed and approved by the author. Subsequent edits were made through prompted revisions in the same session.
