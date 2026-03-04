# AGENTS.md

Instructions for AI agents working in this repository.

## Repository Overview

This is a GitHub Pages site for THE BUTTE FORGE: EMBEDDED SYSTEMS & AI, a student club at Montana Tech. The site is built with Jekyll using the minima theme and served via GitHub Pages. Content is authored in Markdown.

## Repository Structure

- `pages/` - Site pages (Markdown content served by Jekyll)
  - `pages/index.md` - Main landing page (permalink: `/`)
  - `pages/about/` - About section
    - `purpose.md` - Purpose and objectives
    - `team.md` - Leadership team
    - `montana-tech.md` - Alignment and institutional support
  - `pages/departments/` - Department pages
    - `software.md` - Software Engineering
    - `hardware.md` - Hardware Engineering
    - `modeling.md` - Modeling & AI
    - `systems.md` - Systems & Operations
  - `pages/activity/` - Activity section
    - `meetings.md` - Meeting notes
    - `status.md` - Project progress tracker
- `_config.yml` - Jekyll configuration
- `_layouts/default.html` - Base HTML layout (wraps every page)
- `_includes/header.html` - Shared site header (logo + navigation)
- `_includes/footer.html` - Shared site footer (copyright + description)
- `_includes/icons/` - SVG icon partials (included inline by Jekyll)
- `assets/css/style.scss` - Custom styles (imports minima, then overrides)
- `assets/images/logo.png` - Club logo image (raster)
- `assets/icons/` - Standalone SVG icon source files
- `Dockerfile` - Multi-stage build (Jekyll + nginx) for local preview
- `docker-compose.yml` - Docker Compose config to run the site locally on port 8080
- `Gemfile` - Ruby dependencies for Jekyll / GitHub Pages
- `README.md` - Human-readable project documentation
- `AGENTS.md` - This file (instructions for AI agents; excluded from site build)

## Content Rules

- All site content is written in Markdown, rendered by Jekyll with kramdown.
- Do not use emoji characters in any file.
- Do not use em-dashes (U+2014).
- Do not use en-dashes (U+2013).
- Do not use double hyphens (`--`) as separators; use a single hyphen instead.
- Keep line lengths reasonable (under 120 characters where practical).
- Do not duplicate the header or footer in page content; they are rendered
  automatically by the shared layout.

## Jekyll and Build

- The site uses the `minima` theme. Do not change the theme without explicit approval.
- The `_config.yml` file controls site metadata, theme, and build exclusions.
- Files listed under `exclude` in `_config.yml` are not published to the site. Keep `AGENTS.md`, `Dockerfile`, `docker-compose.yml`, `Gemfile`, and `Gemfile.lock` excluded.
- To test locally, run `docker compose up --build -d` and visit `http://localhost:8080`.
- To stop the local preview, run `docker compose down`.
- **After any change to a Markdown (`.md`) page or `_config.yml`, rebuild the
  container** with `docker compose up --build -d` so the change can be
  verified locally.

## Layouts and Includes (DRY)

- `_layouts/default.html` is the base layout. It includes the shared header
  and footer automatically. All pages should use `layout: default` in their
  front matter.
- `_includes/header.html` renders the logo, site title, and navigation links.
  Navigation is driven by the `nav` list in `_config.yml`, which defines
  dropdown groups and their child pages.
- `_includes/footer.html` renders the copyright and site description.
  Footer navigation mirrors the `nav` structure from `_config.yml`.
- To change the header or footer site-wide, edit the corresponding file in
  `_includes/`. Do not duplicate header/footer content in individual pages.

## Adding New Pages

1. Create a new `.md` file inside the appropriate `pages/` subdirectory
   (e.g., `pages/about/`, `pages/departments/`, `pages/activity/`).
2. Add front matter at the top with `layout: default`, a `title`, and a
   `permalink` matching the subdirectory structure:
   ```
   ---
   layout: default
   title: Page Title
   permalink: /section/page-title.html
   ---
   ```
3. Add the page path to the appropriate group under the `nav` list in
   `_config.yml` so it appears in the dropdown navigation.
4. Do not place site pages in the repository root. Only infrastructure files
   (`AGENTS.md`, `README.md`, etc.) belong in the root.
5. Do not add `AGENTS.md`, `README.md`, or other infrastructure files to
   `nav`.

## Git Practices

- Write clear, concise commit messages.
- Do not commit build artifacts or the `_site/` directory.
- The `.git/` directory should never be modified directly.

## Things to Avoid

- Do not introduce JavaScript or external CSS unless explicitly requested.
- Do not remove or overwrite the club logo without approval.
- Do not change the site title or description in `_config.yml` without approval.
- Do not add tracking scripts or analytics without explicit approval.
- Do not use emoji or decorative Unicode characters in Markdown files.
- Do not use em-dashes or en-dashes anywhere in the repository.

## SVG Icons

- Never inline SVG markup directly in HTML templates. Always break SVGs out
  into separate files.
- Standalone SVG source files go in `assets/icons/` (e.g.,
  `assets/icons/icon-email.svg`).
- For SVGs that need to be rendered inline in layouts or includes, create a
  corresponding partial in `_includes/icons/` (e.g.,
  `_includes/icons/email.html`) and use `{% include icons/email.html %}`.
- The `_includes/icons/` partials may include presentation attributes like
  `class`, `width`, and `height` so they render correctly in context.
- Do not embed raw `<svg>` tags in `_includes/header.html`,
  `_includes/footer.html`, or any layout file.
