# Copilot instructions for Meridian

Purpose
- This repository is a minimal static frontend (single HTML landing page with CSS).
- Primary files: `signin.html`, `input.css`, `output.css`.

Big picture
- `signin.html` is the entry point; it loads Tailwind from the CDN (`https://cdn.tailwindcss.com`) and includes inline custom styles for the landing UI.
- `input.css` contains Tailwind directives (`@tailwind base; @tailwind components; @tailwind utilities;`) and uses `@apply` for a custom class — indicating an optional local Tailwind build flow.
- `output.css` is intended as the compiled CSS target but is currently empty in the workspace.

What to do when editing styles
- Quick edits to layout or classes: update `signin.html` (it uses CDN Tailwind, so changes to classes apply immediately in the browser).
- If you prefer an authoring/build flow (recommended for `@apply` use): edit `input.css` and generate `output.css` using the Tailwind CLI. Example command the developer typically runs locally:

  npx tailwindcss -i input.css -o output.css --minify

- Note: this repo has no `package.json` or `tailwind.config.js` checked in. Before running a local build, ask whether to add a Node toolchain or keep using CDN. If adding a build, create `package.json` and `tailwind.config.js` to control content purge and customizations.

Project-specific patterns and conventions
- Visual styles are often created inline in `signin.html`'s `<style>` block for quick prototyping (see `.meridian-text` and `.landing-bg`). Prefer small, targeted changes there for fast iterations.
- `input.css` shows an attempt to centralize Tailwind customizations; use it for shared utilities and `@apply` rules if a build step is adopted.

Integration points and checks for agents
- No server-side code, no tests, and no build scripts were found. Confirm with the user before adding or modifying build/config files.
- If you add scripts or dependencies, update the repo root with `package.json` and document build steps in `README.md`.

When uncertain, ask the user
- If you need to run or add a build step, ask whether to: (A) keep using CDN Tailwind (no build files), or (B) add a Node/Tailwind build (I can scaffold `package.json` and `tailwind.config.js`).

Examples from the codebase
- CDN Tailwind usage: see the `<script src="https://cdn.tailwindcss.com"></script>` line in `signin.html`.
- `input.css` uses `@tailwind` directives and an `@apply` example for `.my-custom-style`.

Keep changes discoverable
- When adding config or build files, include a short `README.md` or update this file to record commands, so future agents won't ask again.

If anything here is unclear or you want the repository to adopt a build pipeline, tell me which option you prefer and I'll update files accordingly.
