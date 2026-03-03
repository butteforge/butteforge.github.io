# THE BUTTE FORGE: EMBEDDED SYSTEMS & AI

Official website for THE BUTTE FORGE: EMBEDDED SYSTEMS & AI, a student club
at Montana Tech.

Live site: [https://butteforge.github.io](https://butteforge.github.io)

## About

This repository hosts the source for our club website, built with
[Jekyll](https://jekyllrb.com/) and the
[minima](https://github.com/jekyll/minima) theme. GitHub Pages automatically
builds and deploys the site on every push to the main branch.

## Local Development

You need [Docker](https://www.docker.com/) installed.

```bash
# Build and start the site locally
docker compose up --build -d

# View the site
open http://localhost:8080

# Stop the local server
docker compose down
```

The Docker setup uses a multi-stage build: Jekyll renders the Markdown into
HTML (mirroring GitHub Pages), then nginx serves the static files.

## Project Structure

| File / Directory   | Purpose                                          |
|--------------------|--------------------------------------------------|
| `index.md`         | Main landing page                                |
| `_config.yml`      | Jekyll configuration (theme, navigation, etc.)   |
| `assets/images/logo.png` | Club logo (raster)                          |
| `Gemfile`          | Ruby dependencies for Jekyll / GitHub Pages      |
| `Dockerfile`       | Multi-stage build for local preview              |
| `docker-compose.yml` | Docker Compose config (serves on port 8080)   |
| `AGENTS.md`        | Instructions for AI coding agents                |
| `README.md`        | This file                                        |

## Adding a New Page

1. Create a new `.md` file in the repository root (e.g., `about.md`).
2. Add it to the `header_pages` list in `_config.yml` so it appears in the
   site navigation.
3. End the page with the copyright footer:
   `(c) 2026 THE BUTTE FORGE: EMBEDDED SYSTEMS & AI`

## Writing Guidelines

- Write content in Markdown (kramdown flavor).
- Do not use emoji or decorative Unicode characters.
- Do not use em-dashes or en-dashes. Use `--` or `-` instead.
- Keep lines under 120 characters where practical.
- Do not add JavaScript, external CSS, or tracking scripts without approval.

## Contributing

1. Fork or clone the repository.
2. Create a feature branch.
3. Make your changes and test locally with Docker.
4. Open a pull request with a clear description of what changed and why.

## License

(c) 2026 THE BUTTE FORGE: EMBEDDED SYSTEMS & AI
