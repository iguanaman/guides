Public repo of single-file HTML reference guides/apps, hosted via GitHub Pages.

## Purpose

Each guide is a mega-guide for its topic — consolidates strategy/insight scattered across wikis/forums/blogs into one place, so the reader never needs to look elsewhere.
Not a reference/rulebook mirror — skip stats, card text, mechanics-as-written, or anything findable in-game or in the manual. Cover oft-repeated community strategy/advice AND notable insight from individual sources (with attribution where it adds credibility) AND general tips/tricks (secondary focus).
When writing guide content, teach transferable insight, not formulas — WHY a play/build/approach is strong, WHEN it applies, the tradeoffs and situational exceptions. Reader should come away able to reason about novel situations, not just follow a script.
Don't reproduce step-by-step walkthroughs (turn-by-turn openers, exact build orders, "do A then B then C"); teach the principle behind them — why this opener, what conditions favor it, how to adapt when conditions differ.
Depth over brevity — go deep on strategy and edge cases; surface-level summaries defeat the purpose. Prefer thorough over concise for guide content itself (this rule doesn't apply to CLAUDE.md/skill files).

## Structure

Each guide lives in its own subfolder (e.g. `sunless-sea/`) — one self-contained `.html` file per guide.
No build system — HTML, CSS, JS, and data all live in that single file.
Each guide subfolder has its own `CLAUDE.md` for guide-specific details (see `sunless-sea/CLAUDE.md`).
Each guide's design/layout/structure is independent — fit it to that guide's topic, not to other guides in this repo. When working on a guide, don't open, check, or reference another guide's subfolder.

## Guides

- `sunless-sea/` — Sunless Sea compendium (ports, bestiary, items, officers, gameplay, lore)
- `spirit-island/` — Spirit Island strategy guide (per-spirit strategy, mechanics deep dives, tips/tricks)
- `feast-for-odin/` — A Feast for Odin strategy guide, base game + Norwegians expansion (occupations, tableau optimization, scoring strategy)
- `ark-nova/` — Ark Nova strategy guide (zoo layout, card engine, appeal/conservation balance, action strategy)
- `fields-of-arle/` — Fields of Arle strategy guide (worker placement, land reclamation, building engine, seasonal planning)
- `balatro/` — Balatro strategy guide (joker synergies, deckbuilding, scoring math, run planning across stakes)

## Git

Never use branches — commit directly to `master`.
Only commit when explicitly asked.
Commit requested → also push.

## Conventions

No external dependencies/frameworks beyond CDN-hosted assets (e.g. images) — keep each guide deployable by opening the HTML file directly or via GitHub Pages.
Every guide sets `html{font-size:18px}` — root font-size is 18px, not the browser-default 16px, so `1rem`=18px.
New guide → new subfolder, own `index.html` or descriptively-named `.html` file.
New guide → add a card linking to it in root `index.html`.
New guide on a topic → use the `new-guide` skill (`.claude/skills/new-guide/`); it dispatches `guide-research-finder` (writes `{guide}/.research/_sources.md`) then runs `guide-research-distiller` sequentially per row (`.claude/agents/`) for sourcing.
`{guide}/.research/_sources.md` = finder's source table (`slug | title | url | note`); slug is category-prefixed kebab-case (`spirit-…`, `mechanic-…`) and is the distiller's output filename + diff key.
`{guide}/.research/*.md` are gitignored scratch from guide research — not committed, not a source of truth once stale.
