
# Observability Workflow Presentation

This project contains a Slidev presentation that explores how AI agents can automate and streamline security and observability workflows for engineering teams. The deck covers:

- The hidden cost of context switching and reactive work
- How AI can triage vulnerabilities, investigate bugs, and generate structured reports
- Real-world examples of automating CVE management and incident analysis
- Lessons learned and practical implementation tips

## Running the Presentation Locally

To view or edit the presentation on your machine:

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Start the Slidev development server:**
   ```bash
   npm run dev
   ```
   This will open the presentation in your browser with hot-reloading for live edits.

3. **Build the presentation for production:**
   ```bash
   npm run build
   ```
   The static site will be output to the `dist` folder.

## Project Structure

- `slides.md` – Main Slidev presentation source (edit this file to update slides)
- `package.json` – Project scripts and dependencies
- `assets/` – Images and media used in the slides

## Deployment

The presentation is automatically deployed to GitHub Pages via GitHub Actions on every push to `main`.

- **Live URL:** [https://acusset.github.io/observability-workflow/](https://acusset.github.io/observability-workflow/)
- The workflow builds the deck with the correct base path and uploads the `dist` folder

## Development Notes

- Keep local secrets in environment files that are not committed.
- Commit only source, configuration templates, and documentation.
- Extend `.gitignore` if your stack introduces additional generated files.
