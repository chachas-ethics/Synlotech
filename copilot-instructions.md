# Copilot / AI Agent Instructions

This repository is a small static website built with HTML and Tailwind CSS. The goal of this file is to give AI coding agents exactly the repository-specific knowledge needed to be productive without guessing.

- Quick summary: Static HTML files in `src/`; Tailwind source is `src/input.css` and the generated CSS is `src/output.css`. The Tailwind CLI is used (see `package.json` `dev` script).

- Key files:
  - `src/index.html` — main entry page and example of page structure
  - `src/*.html` — content pages (many standalone HTML files)
  - `src/input.css` — Tailwind input / authorable CSS (edit this)
  - `src/output.css` — generated CSS (do NOT edit directly)
  - `tailwind.config.js` — present (currently empty) for Tailwind config
  - `package.json` — contains `dev` script: `npx @tailwindcss/cli -i ./src/input.css -o ./src/output.css --watch`
  - `src/thumbnails/` — image assets used by pages (examples: `aiill.avif`, `graphics.avif`)

- Development workflow (discoverable):
  - Start the Tailwind watcher to regenerate CSS while editing:

    npm run dev

  - There is no bundled dev server in the repo. Preview pages by opening the HTML files in a browser, or run a lightweight static server (e.g., the VS Code Live Server extension or `npx http-server`) alongside the `npm run dev` watch.

- Project-specific conventions and gotchas:
  - `src/output.css` is generated; any style changes should be made in `src/input.css` (or `tailwind.config.js`) then re-run `npm run dev`.
  - Pages are plain HTML fragments (no SPA framework). Changes to layout may require editing multiple files under `src/`.
  - File naming: there are similarly-named files with different casing (e.g., `graphic.html` and `Graphics.html`). On Windows this is not enforced by the filesystem, so avoid renaming only by case — treat names as effectively case-insensitive.
  - Tailwind configuration is available at `tailwind.config.js` (currently blank). Add custom utilities or theme extensions here if needed and restart the watcher.

- Integration points and dependencies:
  - Only runtime dependencies are Tailwind CLI and Tailwind itself (see `package.json`). No backend or external APIs are present in the repo.

- How an AI agent should make edits (practical rules):
  1. Prefer editing `src/input.css` for styling changes; run `npm run dev` to regenerate `src/output.css` and include the regenerated output in PRs only if necessary for preview screenshots — mark generated files clearly in the PR description.
  2. For content/layout changes, update the relevant `src/*.html` files. Search for repeated header/footer patterns to update all pages consistently.
  3. When adding images, put them in `src/thumbnails/` and reference them with relative paths.
  4. Do not add build tooling without mentioning it in the PR description; this repo uses minimal tooling intentionally.

- Examples from this repo:
  - To change the primary CSS, edit `src/input.css` and run `npm run dev` (Tailwind CLI regenerates `src/output.css`).
  - To preview `index.html`, open it in a browser or serve the `src` folder with a static server while `npm run dev` runs.

If anything here is unclear or you want additional conventions documented (naming rules, PR expectations, or testing guidance), tell me which areas to expand and I will update this file.
