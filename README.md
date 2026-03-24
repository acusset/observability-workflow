# observability-workflow

Slidev presentation for the observability workflow project.

## Getting started

1. Install dependencies:

   ```bash
   npm install
   ```

2. Start the Slidev dev server:

   ```bash
   npm run dev
   ```

3. Build the presentation:

   ```bash
   npm run build
   ```

## Project structure

- `slides.md` – Slidev presentation source
- `package.json` – Slidev scripts and dependencies

## Deployment

The presentation is deployed to GitHub Pages by GitHub Actions on every push to `main`.

- Published URL: `https://acusset.github.io/observability-workflow/`
- The workflow builds the deck with the repository base path before uploading `dist`

## Development

- Keep local secrets in environment files that are not committed.
- Commit only source, configuration templates, and documentation.
- Extend `.gitignore` if your stack introduces additional generated files.
