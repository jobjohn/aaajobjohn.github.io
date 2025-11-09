# Repository Guidelines

## Project Structure & Module Organization
- `index.html` hosts the single-page layout loaded by GitHub Pages; edit sections here when copy or DOM structure changes.
- `src/style.css` contains all custom styles and font declarations—group related selectors and favor utility classes over inline styles.
- External resets, fonts, and assets are referenced via CDN; document any new dependency links in the `<head>` block to keep reviewers aware.

## Build, Test, and Development Commands
- `python3 -m http.server 4173` (run from repo root) serves the site locally for quick visual checks; stop with `Ctrl+C`.
- `npx serve .` is an alternative static server if Node tooling is preferred; install `serve` globally only if you already rely on npm workflows.
- `npm test` currently fails intentionally; update the script once automated checks are introduced so CI signals remain reliable.

## Coding Style & Naming Conventions
- HTML uses two-space indentation; keep attributes on new lines when tags exceed ~80 chars for readability.
- CSS follows kebab-case class names (`.cardcontainer`, `.cardtext`); prefer semantic prefixes (`.section-hero`, `.btn-primary`) when adding components.
- Maintain gradient palettes and font stacks defined in `style.css`; extract shared values into CSS custom properties before adding duplicate hex codes.
- Run `npx prettier --write index.html src/style.css` before commits if you introduce multi-line edits; abide by Prettier defaults (2 spaces, double quotes in HTML).

## Testing Guidelines
- No formal test suite exists; validate changes by loading the local server in modern browsers (Chrome, Firefox, Safari) and confirming layout parity.
- Record responsive behavior at 360px, 768px, and 1280px widths; attach screenshots to PRs when adjusting typography or spacing.
- When adding JavaScript or pipeline tooling, include unit tests (e.g., Vitest) under `tests/` and wire them into `npm test`.

## Commit & Pull Request Guidelines
- Follow the existing short, imperative commit style seen in `git log` (e.g., `add hero gradient`, `fix card spacing`).
- Each PR description should summarize the visual impact, list affected files, and link related issues; include before/after images for UI adjustments.
- Ensure branch names pair scope and intent (`feature/card-hover`, `fix/font-loading`); rebase onto main before requesting review.

## Deployment & Configuration Tips
- The `gh-pages` branch (or repository default) serves content directly from this root; avoid build artifacts or large binaries.
- For new assets, compress images and place them under `src/assets/` (create the folder if needed) to keep the root uncluttered.
