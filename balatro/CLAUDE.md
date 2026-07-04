Balatro strategy guide — single-file `index.html`.

## Structure
Sticky top-tab nav, 6 tabs, vanilla JS tab-switch (`nav.tabs button[data-tab]` ↔ `.panel#panel-{tab}`):
1. Scoring & Scaling — Chips×Mult, Ante-3 scaling deadline, 4 Joker roles (accordion), secondary scaling.
2. Hands & Archetypes — 4 build lanes, per-hand accordion (12 hands), High Card Gold-Stake template, Flush arc, Plasma endgame math.
3. Jokers & Synergy — carry-engine principle, Baron/Steel-King worked example, copy-joker chaining, shared-condition stacking, manageable-downside principle, edition jokers.
4. The Run: Economy & Shop — interest engine, reroll framework, voucher priority, consumable timing, skip-or-play.
5. Antes, Bosses & Stakes — ante arc, boss-blind accordion (11 bosses), stakes ladder table, 15-deck accordion.
6. Tips & Mistakes — beginner mistakes, non-obvious plays.

Within-tab drill-down = `.accordion` > `.acc-item` (toggle `.open` on header click) > `.acc-header` + `.acc-body > .acc-body-inner`.
Cross-tab links = `<a data-goto="{tab}">` — same click handler switches nav+panel active state (see inline `<script>`).

## Content voice
No named-source attribution (no wiki/Reddit author credit) — strategy stated in guide's own voice per root `CLAUDE.md` Purpose rules.
Source material: `.research/*.md` (gitignored, 37 distilled files) — not consulted again once content is written; re-derive from this file + the HTML for future edits.
