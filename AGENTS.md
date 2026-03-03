# AGENTS.md

Instructions for AI agents working in this repository.

## Repository Overview

This is a GitHub Pages site for THE BUTTE FORGE: EMBEDDED SYSTEMS & AI, a student club at Montana Tech. The site is built with Jekyll using the minima theme and served via GitHub Pages. Content is authored in Markdown.

## Repository Structure

- `index.md` -- Main landing page
- `_config.yml` -- Jekyll configuration
- `_layouts/default.html` -- Base HTML layout (wraps every page)
- `_includes/header.html` -- Shared site header (logo + navigation)
- `_includes/footer.html` -- Shared site footer (copyright + description)
- `assets/css/style.scss` -- Custom styles (imports minima, then overrides)
- `assets/images/logo.png` -- Club logo image (raster)
- `Dockerfile` -- Multi-stage build (Jekyll + nginx) for local preview
- `docker-compose.yml` -- Docker Compose config to run the site locally on port 8080
- `Gemfile` -- Ruby dependencies for Jekyll / GitHub Pages
- `README.md` -- Human-readable project documentation
- `AGENTS.md` -- This file (instructions for AI agents; excluded from site build)

## Content Rules

- All site content is written in Markdown, rendered by Jekyll with kramdown.
- Do not use emoji characters in any file.
- Do not use em-dashes (U+2014).
- Do not use en-dashes (U+2013).
- Keep line lengths reasonable (under 120 characters where practical).
- Do not duplicate the header or footer in page content; they are rendered
  automatically by the shared layout.

## Jekyll and Build

- The site uses the `minima` theme. Do not change the theme without explicit approval.
- The `_config.yml` file controls site metadata, theme, and build exclusions.
- Files listed under `exclude` in `_config.yml` are not published to the site. Keep `AGENTS.md`, `Dockerfile`, `docker-compose.yml`, `Gemfile`, and `Gemfile.lock` excluded.
- To test locally, run `docker compose up --build -d` and visit `http://localhost:8080`.
- To stop the local preview, run `docker compose down`.

## Layouts and Includes (DRY)

- `_layouts/default.html` is the base layout. It includes the shared header
  and footer automatically. All pages should use `layout: default` in their
  front matter.
- `_includes/header.html` renders the logo, site title, and navigation links.
  Navigation is driven by the `header_pages` list in `_config.yml`.
- `_includes/footer.html` renders the copyright and site description.
- To change the header or footer site-wide, edit the corresponding file in
  `_includes/`. Do not duplicate header/footer content in individual pages.

## Adding New Pages

1. Create a new `.md` file in the repository root.
2. Add front matter at the top with `layout: default` and a `title`:
   ```
   ---
   layout: default
   title: Page Title
   ---
   ```
3. Add the filename to the `header_pages` list in `_config.yml` if it should
   appear in site navigation.
4. Do not add `AGENTS.md`, `README.md`, or other infrastructure files to
   `header_pages`.

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
