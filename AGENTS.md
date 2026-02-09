# Repository Guidelines

## Project Structure & Module Organization
This project is a static CV site built with Node.js.
- `src/metadata/metadata.js`: main profile content and structured data.
- `src/templates/index.html`: Handlebars template used to generate the page.
- `src/assets/`: static files (CSS, favicon, and other copied assets).
- `src/utils/`: build helpers (Markdown conversion and PDF utilities).
- `src/build.js`: build entry point that renders `dist/index.html` and a PDF.
- `dist/`: generated output only; do not hand-edit.
- `.github/workflows/gh-pages.yml`: CI build and deployment to `gh-pages`.

## Build, Test, and Development Commands
- `npm install`: install dependencies.
- `npm run build`: generate fresh files in `dist/` (HTML + PDF).
- `npm start`: run a local live server with file watching (`dist` preview).
- `npm run watch`: rebuild on file changes without starting the server.
- `npm run deploy`: build and publish `dist/` via `gh-pages` (manual deploy path).

Example local workflow: `npm install && npm start`, then edit files under `src/`.

## Coding Style & Naming Conventions
Follow `.editorconfig`:
- JavaScript and JSON: 2-space indentation.
- HTML templates: 4-space indentation.
- UTF-8, LF line endings, and final newline required.

Use clear, lower-case file names in `src/` and keep metadata keys descriptive (for example, `workExperience`, `education`, `skills`).

## Testing Guidelines
There is no automated test suite in this repository today. Treat build output validation as the baseline:
- Run `npm run build` before every PR.
- Verify `dist/index.html` renders correctly in the browser.
- Confirm generated PDF layout is readable and does not clip content.

For visual or content-heavy changes, include before/after screenshots or rendered output notes in the PR.

## Commit & Pull Request Guidelines
Recent history uses short, imperative commit messages focused on content updates (for example, `updated cv`, `added new content`). Continue with concise, action-first messages and group related edits.

For PRs:
- Provide a short summary of what changed and why.
- Link related issues/tasks when available.
- Note local verification steps (`npm run build`, `npm start` preview).
- Include screenshots for template/CSS/layout changes.
