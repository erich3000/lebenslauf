# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a CV/resume (Lebenslauf) generator for Jens Ihrig. It builds a static HTML page and PDF from structured data using Handlebars templates. Based on the [cv-template](https://github.com/sneas/cv-template/) project.

Deployed to GitHub Pages at https://erich3000.github.io/lebenslauf/

## Commands

- `npm start` — Build, watch for changes, and serve locally via live-server
- `npm run build` — One-shot build (generates HTML + PDF into `dist/`)
- `npm run deploy` — Build and deploy to GitHub Pages via `gh-pages`

## Architecture

The build pipeline (`src/build.js`) does three things sequentially:

1. Copies `src/assets/` (CSS, favicon) to `dist/`
2. Compiles `src/templates/index.html` (Handlebars template) with data from `src/metadata/metadata.js`, outputting `dist/index.html`
3. Generates a PDF from the built HTML using Puppeteer (A4 format, 2.54cm margins)

**Key files:**

- `src/metadata/metadata.js` — All CV content (personal info, skills, jobs, education). This is the primary file to edit when updating CV content.
- `src/templates/index.html` — Handlebars template with Bootstrap 4 layout. Uses a custom `{{markdown}}` helper to render markdown in content fields.
- `src/assets/styles.css` — Custom styles with separate print/screen media queries and `col-print-*` classes for PDF layout control.
- `src/utils/helpers/markdown.js` — Handlebars helper that converts markdown to HTML.

## Content Format

In `metadata.js`, the `contents` fields accept markdown (rendered via the `{{markdown}}` helper). Skills use `+` characters to indicate proficiency level (e.g., `"+++++"`). The CV language is German.

## Deployment

Pushing to `master` triggers a GitHub Actions workflow (`.github/workflows/gh-pages.yml`) that builds and deploys to the `gh-pages` branch.
