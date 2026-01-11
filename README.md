# 2016 Frank Jamison — Online Resume (Static Site)

This repository is a polished, multi-page resume website built as a static site (HTML/CSS/JavaScript). It emphasizes consistent branding, clean information architecture, and small interactive touches (accordion sections + animated page transitions) while keeping the runtime simple to host anywhere.

## What this demonstrates (recruiter-friendly)

### Design & UX

- **Consistent layout system**: shared header/nav/banner/content/aside/footer structure across all pages.
- **Branding and visual system**: an explicit color palette in CSS and a repeated “cube” motif used in headings and the header.
- **Page-specific hero banners**: each section uses a dedicated banner image (Employment/Education/Skills/Awards/Organizations) for fast orientation.
- **Readable typography**: custom webfonts loaded via `@font-face` with a serif display face for headings.
- **Information hierarchy**: content is grouped into scannable categories and nested sections; long resume content is made navigable with accordions.

### Front-end development

- **Progressive enhancement**: the site renders as plain HTML, then adds interactivity through JavaScript.
- **Two accordion implementations**:
  - jQuery UI accordion for nested list sections (Employment, Skills, Awards, Affiliations).
  - Checkbox-driven accordion markup for Education (`.cd-accordion-menu`) with animated open/close behavior.
- **Animated navigation**: Animsition adds fade-in/fade-out transitions between internal pages.
- **Asset strategy**:
  - Local images for banners/icons.
  - Social icons embedded as base64 data URIs in CSS to reduce extra HTTP requests.
- **Practical HTML details**: `mailto:` and `tel:` links, `alt` text for the profile image, and a straightforward folder layout.

## Pages

- `index.html` — Home / summary + contact info
- `employment.html` — Employment, military, and volunteer history (accordion)
- `education.html` — Formal education and coursework (checkbox accordion)
- `skills.html` — Skills grouped by category (accordion)
- `awards.html` — Awards grouped by category (accordion)
- `affiliations.html` — Organizations/affiliations grouped by category (accordion)

## Tech stack

- HTML5
- CSS (single shared stylesheet)
- JavaScript
- External libraries (loaded via CDN in each HTML page):
  - jQuery 2.2.4
  - jQuery UI 1.11.4
  - Animsition 4.0.2

## Project structure

- `_css/style2.css` — site-wide styles: palette, typography, layout, banners, accordion styling, contact/social styling
- `_javascript/script.js` — jQuery UI accordion initialization + Animsition configuration
- `_javascript/main.js` — Education page checkbox-accordion animation
- `_images/` — banners, icons, profile image
- `_fonts/` — Cantarell, Cardo, Ostrich webfont files + included license texts
- `.vscode/tasks.json` — optional VS Code task to open a local URL in Chrome

## Run locally

### Option A: open directly

Open `index.html` in your browser.

### Option B: run a tiny static server (recommended)

Running a local server avoids browser restrictions and ensures relative assets behave consistently.

- Python:
  - `python -m http.server 8080`
- Node:
  - `npx serve`

Then open the printed URL (typically `http://localhost:8080/`).

### VS Code shortcut (optional)

There’s a VS Code task named **Open in Browser** (see `.vscode/tasks.json`) that opens `http://2016frankjamison.localhost/` in Chrome. This is useful if you already have a local host entry / vhost set up for that domain.

## How it’s built

### Shared layout pattern

Each page follows the same major sections:

- `header#pageHeader` (name + subtitle)
- `nav#mainNav` (section navigation)
- `#banner` (page-specific banner class, e.g. `#banner.skills`)
- `article` (main content)
- `aside` (contact card)
- `footer#pageFooter`

### Interactive content

- List-based accordion sections use `.trackAccordion` and are initialized in `_javascript/script.js`.
- Education uses `.cd-accordion-menu` markup styled in `_css/style2.css` and animated in `_javascript/main.js`.

### Animated page transitions

Animsition is applied to the `.animsition` wrapper and triggers when following links with `.animsition-link`.

## Notes for maintainers

- Navigation is duplicated in each HTML file; if you add/remove a page, update the `<nav>` block everywhere.
- The layout is **desktop-first and fixed-width** (e.g., `body { width: 1280px; }`). If you want modern mobile support, the quickest path is adding a `meta viewport` tag and converting layout to a responsive grid/flex approach.
- This project depends on CDNs for its JS/CSS libraries; for offline deployments, vendor those assets locally and update the `<script>`/`<link>` tags.

## Attribution

- Font license files are included in `_fonts/`.
