# 2016 Frank Jamison — Online Resume (Static Site)

A static HTML/CSS/JavaScript “online resume” site with a consistent layout across multiple pages (Employment, Education, Skills, Awards, Affiliations). Pages share the same stylesheet and use a small amount of jQuery-based behavior for page transitions and accordion-style sections.

## Pages

- `index.html` — Home / intro + contact info
- `employment.html` — Employment history (accordion)
- `education.html` — Education history
- `skills.html` — Skills lists (accordion)
- `awards.html` — Awards / achievements
- `affiliations.html` — Organizations / affiliations

## Tech stack

- HTML5 + CSS
- JavaScript
- jQuery + jQuery UI (loaded via CDN in the HTML)
- Animsition (page transition library, loaded via CDN in the HTML)
- Local fonts in `_fonts/` loaded via `@font-face`

## Project structure

- `_css/`
  - `style2.css` — primary stylesheet referenced by the pages
- `_javascript/`
  - `script.js` — site behavior (jQuery UI accordion + Animsition initialization)
  - `main.js` — checkbox accordion behavior for the `cd-accordion-menu` markup (used on `education.html`)
- `_images/` — images used by layout and content (logos, profile image, etc.)
- `_fonts/` — webfont files + font license texts

## How it works

### Shared layout
Each HTML page uses the same basic structure:

- Header with name + subtitle
- Main navigation linking the other pages
- `#banner` section with a page-specific title
- Main `article` content
- Optional `aside` (contact info on the home page)
- Footer

### Accordion sections
Some pages (notably `employment.html` and `skills.html`) use jQuery UI’s accordion widget.

- Accordion markup is based on nested `<ul class="trackAccordion"> ... </ul>` lists.
- Behavior is initialized in `_javascript/script.js`.

`education.html` uses a checkbox-driven accordion markup (`.cd-accordion-menu`) initialized by `_javascript/main.js`.

### Page transitions
The site uses Animsition for fade-in/fade-out transitions when following internal navigation links.

- The wrapper element is `.animsition`.
- Links intended to transition use the `.animsition-link` class.
- The configuration lives in `_javascript/script.js`.

## Local preview

Because this is a static site, you can preview it in either of these ways:

1) Open `index.html` directly in a browser.

2) Run it with a local static file server (recommended for consistent relative-path behavior):

- Python (if installed):
  - `python -m http.server 8080`
- Node.js (if installed):
  - `npx serve`

After starting a server, open the address printed by the tool in your terminal.

## Editing guide

### Update content
- Home page text and contact information are in `index.html`.
- Section content for each page is inside the main `<article>` element.

### Update navigation
- Navigation is hard-coded into each HTML page.
- If you add/remove a page, you’ll need to update the `<nav id="mainNav">` block on every page to keep the menu consistent.

### Update styling
- Most styling is in `_css/style2.css`.

### Images and fonts
- Put new images in `_images/` and reference them with relative paths like `_images/your-file.png`.
- Fonts are configured at the top of `_css/style2.css` using `@font-face` and served from `_fonts/`.

## Deployment

This site can be deployed anywhere that serves static files:

- Copy the entire folder contents (HTML + `_css/`, `_javascript/`, `_images/`, `_fonts/`) to your hosting provider.
- Ensure the server serves `index.html` as the default document.

## Notes / troubleshooting

- This site depends on external CDNs for jQuery, jQuery UI, and Animsition. If you need offline operation, you’ll want to vendor those libraries locally and update the `<script>` / `<link>` tags.
- Accordion behavior requires jQuery UI to load successfully.

## License / attribution

- Font licenses (as provided) are in `_fonts/`.
- Other site content and assets follow whatever licensing/ownership applies to this repository’s contents.
