# AGENTS.md

## Project Overview

Personal portfolio website for Joshua Young, deployed directly to GitHub Pages (`joshua-y.github.io`) from the `main` branch.

- **Stack:** Vanilla HTML, CSS, and JavaScript — no build step, bundler, framework, or package manager.
- **External assets:** Font Awesome 6.0.0 loaded via cdnjs in `index.html`.

## Repository Structure

```text
.
├── index.html   # Single-page layout (navbar, hero, about/skills, experience, projects, footer)
├── styles.css   # Theme CSS variables, layout, component styles, animations, responsive rules
└── script.js    # Theme toggle (localStorage + prefers-color-scheme), smooth scroll, scroll reveal
```

## Local Development & Verification

There are no dependencies to install or build commands to run. Serve the repository root with any static HTTP server to preview changes:

```bash
python3 -m http.server 8000
```

When verifying changes manually, check:
1. Both light and dark themes (including persistence across reload via `localStorage`).
2. Desktop and mobile (`<= 768px`) viewports.
3. Navbar anchor navigation, smooth scrolling, and section reveal animations.
4. No browser console errors or broken external links/icons.

Pushing to `main` deploys directly to GitHub Pages.

## Conventions & Guidelines

- **Stay zero-build:** Keep the site in vanilla HTML, CSS, and JS. Do not introduce npm, bundlers, CSS preprocessors, or JS frameworks unless explicitly requested.
- **Formatting:** Use 4-space indentation across `index.html`, `styles.css`, and `script.js`.
- **Theming:** Use the CSS custom properties defined in `:root` and `[data-theme="dark"]` in `styles.css` so new or updated UI works in both light and dark modes.
- **Content patterns:** Reuse existing markup and class structures when updating content:
  - Skills: `.skill-category` with `.skill-tags` `<span>` items
  - Work history: `.experience-item` with `.experience-header` and `.experience-details`
  - Projects: `.project-item` with `.project-links`
- **Navigation sync:** Keep section `id` attributes (`#home`, `#about`, `#experience`, `#projects`) aligned with `.nav-links` `href` values in `index.html`.
- **Personal content:** Never invent or modify personal details, resume/social URLs, job descriptions, or project details unless explicitly asked.

## Known Quirks

- `styles.css` references `var(--border-color)` on `.skill-tags span`, which is not currently defined in `:root` or `[data-theme="dark"]`.
- `styles.css` contains some unused/legacy rules (e.g., `.network-graph`, `.graph-svg`, `#contact-form`, `.email-link`, and duplicate `.contact-content` / `.experience-item li` selectors). Avoid building on unused selectors, and avoid unrelated cleanup unless requested.
- Below `768px`, `.nav-links` is hidden via `display: none` with no mobile drawer/menu.
