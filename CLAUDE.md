Public repo of single-file HTML reference guides/apps, hosted via GitHub Pages.

## Purpose

Each guide is a mega-guide for its topic — consolidates strategy/insight scattered across wikis/forums/blogs into one place, so the reader never needs to look elsewhere.
Writing or editing any guide's HTML content → use the `write-guide-content` skill (`.claude/skills/write-guide-content/`) first.

## Structure

Each guide lives in its own subfolder (e.g. `sunless-sea/`) — one self-contained `.html` file per guide.
No build system — HTML, CSS, JS, and data all live in that single file.
Each guide subfolder has its own `CLAUDE.md` for guide-specific details (see `sunless-sea/CLAUDE.md`).
Every guide shares one visual design — the Lantern theme, see `.claude/lantern-theme.md` — light/dark toggle, same palette/type/nav/modal. Content structure (tabs, sections, layout of strategy content) stays independent per guide, fit to that topic.

## Guides

- `sunless-sea/` — Sunless Sea compendium (ports, bestiary, items, officers, gameplay, lore)
- `spirit-island/` — Spirit Island strategy guide (per-spirit strategy, mechanics deep dives, tips/tricks)
- `feast-for-odin/` — A Feast for Odin strategy guide, base game + Norwegians expansion (occupations, tableau optimization, scoring strategy)
- `ark-nova/` — Ark Nova strategy guide (zoo layout, card engine, appeal/conservation balance, action strategy)
- `fields-of-arle/` — Fields of Arle strategy guide (worker placement, land reclamation, building engine, seasonal planning)
- `balatro/` — Balatro strategy guide (joker synergies, deckbuilding, scoring math, run planning across stakes)
- `this-war-of-mine/` — This War of Mine: The Board Game survival guide (scavenging, shelter management, moral choices, house rules)
- `nusfjord/` — Nusfjord strategy guide (fishing company management, worker placement, building engine, share strategy)

## Git

Never use branches — commit directly to `master`.
Only commit when explicitly asked.
Commit requested → also push.

## Board Game Preferences

- Solo main mode: heavier the better, no ceiling.
- Prefer puzzly, low-randomness solo modes (Uwe Rosenberg style) — game as solvable system. Dislike bot/AI-opponent solo modes (David Turczi style).
- Strategy over tactics: full info upfront, plan whole game, no round-to-round re-assessment.
- Tolerate randomness more in casual multiplayer — house-rule scope below is solo-only.
- House-rule solo play to remove randomness — score reflects skill not luck, for replayability & tracking improvement across attempts.
- House-rule philosophy: stay close to original rules, break only when it helps & doesn't break the game.
- Prefer self-blocking (Feast for Odin: block own board) over randomized blocking (automa/die/card draw).
- House-rule toolbox: reveal hidden info (face-up decks, sequences shown upfront); draw-then-choose (draw N, pick 1; or pick freely for static setup) — never when cards drive an opponent (weakens it / collapses to solitaire); average-out dice (replace roll with expected value); fix orders/lock setups for comparable replays.
- Choice quantification for draw-then-choose: E[best of N+1] ≈ (N+1)/(N+2), sharp diminishing returns — default N=3 (3 laid out + face-up deck top = 4 choices); N=1-2 for flexible needs, N=3-4 when hunting a specific card; N = cards laid out, not total choices.
- Per-game house-rule configs (Static = deterministic full-info puzzle, reveal-only = lighter fresher-but-less-comparable variant) tracked outside this repo, one doc per game — ask if relevant one isn't visible.

## Conventions

No external dependencies/frameworks beyond CDN-hosted assets (e.g. images) — keep each guide deployable by opening the HTML file directly or via GitHub Pages.
Every guide sets `html{font-size:18px}` — root font-size is 18px, not the browser-default 16px, so `1rem`=18px.
Top-level tab nav follows `.claude/lantern-theme.md`'s nav spec: `flex-wrap:nowrap` + `overflow-x:auto` + `scroll-behavior:smooth` — never `flex-wrap:wrap` (stacks tabs vertically and they stay on-screen permanently on narrow viewports, worst with `position:sticky`). Buttons get `flex:0 0 auto;white-space:nowrap`. Center tabs only above the width they start overflowing (`@media(min-width:900px){justify-content:center}`), `flex-start` below it.
New guide → new subfolder, own `index.html` or descriptively-named `.html` file.
New guide → add a card linking to it in root `index.html`.
New guide on a topic → use the `new-guide` skill (`.claude/skills/new-guide/`); it dispatches `guide-research-finder` (writes `{guide}/.research/_sources.md`) then runs `guide-research-distiller` sequentially per row (`.claude/agents/`) for sourcing.
`{guide}/.research/_sources.md` = finder's source table (`slug | title | url | note`); slug is category-prefixed kebab-case (`spirit-…`, `mechanic-…`) and is the distiller's output filename + diff key.
`{guide}/.research/*.md` are gitignored scratch from guide research — not committed, not a source of truth once stale.
Reading `.research/*.pdf`: use `pdftotext` (via Bash), not the Read tool's page-range rendering — `pdftoppm`/poppler isn't installed in this environment.
