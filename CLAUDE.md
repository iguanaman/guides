Public repo of single-file HTML reference guides/apps, hosted via GitHub Pages.

## Structure

Each guide lives in its own subfolder (e.g. `sunless-sea/`) — one self-contained `.html` file per guide.
No build system — HTML, CSS, JS, and data all live in that single file.
Subfolder may have its own `CLAUDE.md` for guide-specific details.

## Conventions

No external dependencies/frameworks beyond CDN-hosted assets (e.g. images) — keep each guide deployable by opening the HTML file directly or via GitHub Pages.
New guide → new subfolder, own `index.html` or descriptively-named `.html` file.
