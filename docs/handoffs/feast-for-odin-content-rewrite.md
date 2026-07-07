# Job: rewrite Feast for Odin guide content via sequential per-topic agents

Rewrite the content of `feast-for-odin/index.html` using the refreshed `.research/*.md` files. Keep existing HTML/CSS structure (tab layout, card-grid markup, section IDs) — this is a content rewrite, not a redesign. Do NOT touch the action board layout (locked per `feast-for-odin/CLAUDE.md`). Load the `write-guide-content` skill before writing any section — it governs collation rules (don't summarize away distinct claims, attribute disagreements, teach transferable insight not scripts, skip base-game/multiplayer-only info).

**Solo-only filter**: only content, all expansions (Norwegians + Harvest + minis). Cut info that's explicitly base-game-only or multiplayer-only; when unsure whether something applies, leave it in.

## Scope — sections to rewrite

- `#paths` (Strategy Paths, `index.html:631-645`) — 9 path cards: Cattle, Sheep, Horse, Pig, Hunting & Whaling, Raiding & Pillaging, Ore Crafting, Longhouses, Emigration.
- `#islands` (`index.html:647-683`) — three tiers: One-Viking, Two-Viking, Three-Viking islands (~20 boards total).
- `#sheds` (Artisan Sheds, `index.html:685-696`) — 6 shed-pair cards.
- `#tips` (`index.html:1024-1140`) — 5 `<details>` subsections: General & Beginner Advice, Tile Adjacency, Food Economy, Negative-Point Coverage, Solo Play. Skip "Commonly Missed Rules" subsection — user not interested in rules/mechanics content, leave that subsection as-is.

## Explicitly out of scope

- `#occupations` (Occupation Cards tab) — skip. Too many cards, no single source covers all of them coherently; not worth a rewrite pass.
- `#setup` — skip, it's rulebook-derived reference, not guide/strategy content.
- `#actionboard`, `#campaign`, `#houserules` — leave untouched (action board is locked; campaign is CSV-driven; house rules are the user's personal solo ruleset, not community-sourced content).
- Rules/mechanics content generally — user is not interested in rules-clarification content in this guide. Don't pull `mechanic-commonly-missed-rules-boardoflife.md` into any section; skip the "Commonly Missed Rules" tips subsection entirely. Frame shed/path/island content around strategy and value judgment, not rules corrections.

## Why sub-agents, and why sequential

User's directive: doing this in one pass (read all ~45 research files, then edit the whole guide) blows the context budget and produces confused/averaged-out writing. Instead: break into tabs, decide per-tab whether it further splits by sub-topic, then dispatch one agent at a time — each agent reads only its relevant `.research/*.md` slice and edits only its section of `index.html`. Review each diff before starting the next agent so errors don't compound across sections.

## Planned agent breakdown (10-11 dispatches)

Research files live in `feast-for-odin/.research/` (gitignored scratch, not committed — see project CLAUDE.md). Cross-reference `.research/_sources.md` for what each file covers.

**Strategy Paths — 5 agents** (group related/small paths together, split large ones out):
1. Cattle + Horse — sources: `strategy-animal-cattle-boardoflife.md`, `strategy-animal-cattle-easier-bgg.md`, `strategy-animal-horse-boardoflife.md`.
2. Sheep — sources: `strategy-animal-sheep-boardoflife.md`, `strategy-animal-sheep-easier-bgg.md`, `strategy-green-shadow-tiles-bgg.md` (green tile adjacency ties directly into sheep's green-tile-glut problem).
3. Pig — sources: `strategy-animal-pig-boardoflife.md`, `strategy-animal-shortcut-cards-bgg.md` (Livestock Market rush combos).
4. Hunting & Whaling + Raiding & Pillaging — sources: `strategy-raiding-vs-pillaging-mechanics-bgg.md`, `strategy-special-tile-acquisition-bgg.md`, relevant parts of `general-action-infographic-bgg.md`.
5. Ore Crafting + Longhouses + Emigration — sources: `strategy-occupations-combo-power-bgg.md`, `strategy-occupations-combos-bgg.md` (for engine-combo reasoning), `strategy-food-village-size-gamewardbound.md`, `strategy-planning-vs-improvising-gamewardbound.md`, `strategy-home-board-analysis-bgg.md`, `strategy-active-passive-engines-boardoflife.md` (active/passive framework applies across all three).

Note: `strategy-active-passive-engines-boardoflife.md` and `strategy-action-size-priority-boardoflife.md` are cross-cutting framework pieces — relevant to most/all path agents as background, not owned by one.

**Islands — 3 agents, one per Viking-cost tier**, each also reading the cross-cutting valuation sources:
6. One-Viking islands — `strategy-exploration-1v-islands-boardoflife.md`, `strategy-exploration-1p-norwegians-bgg.md`, plus valuation/timing sources below.
7. Two-Viking islands — `strategy-exploration-2v-islands-boardoflife.md`, plus valuation/timing sources below.
8. Three-Viking islands — `strategy-exploration-3v-islands-boardoflife.md`, `strategy-exploration-three-islands-bgg.md`, plus valuation/timing sources below.

Cross-cutting sources relevant to all three island agents: `strategy-exploration-valuation-1-bgg.md`, `strategy-exploration-valuation-2-bgg.md`, `strategy-exploration-vs-houses-bgg.md`, `strategy-exploration-zero-island-bgg.md`, `strategy-tile-size-timing-gamingstrategy.md`. Norwegians-specific per-island color/notes come from `strategy-action-board-1p-bgg.md` and `strategy-isle-of-man-opener-bgg.md`, `strategy-isle-of-mull-opener-bgg.md`, `strategy-isle-of-mull-power-bgg.md`, `strategy-emigration-opener-iceland-bgg.md` (mine these opener/single-island threads for principles, not literal turn-by-turn scripts — see write-guide-content's no-walkthroughs rule).

**Artisan Sheds — 1 agent** (no further split; small topic):
9. Source: `strategy-artisan-shed-choice-boardoflife.md`.

**Tips — 1 agent** (recommend single pass; 5 subsections but heavily overlapping broad sources, don't over-fragment):
10. Sources: `general-forum-highlights-bgg.md`, `general-solo-tips-bgg.md`, `general-solo-192-boardoflife.md`, `strategy-negative-points-raginglevine.md`, `strategy-food-efficiency-bgg.md`, `strategy-food-village-size-gamewardbound.md`, `strategy-planning-vs-improvising-gamewardbound.md`, `strategy-home-board-analysis-bgg.md`, `strategy-action-size-priority-boardoflife.md`, `strategy-tile-size-timing-gamingstrategy.md`, `strategy-green-shadow-tiles-bgg.md`. Do not touch the "Commonly Missed Rules" subsection.

If the Tips agent finds it's too much to hold at once, it can split into two passes itself (e.g. rules-mechanics subsections vs. strategy-advice subsections) — that call is fine to make at execution time.

## Not yet done

None of the actual rewriting has started — this handoff is purely the planning/breakdown output. Next conversation should start at agent #1 (Cattle + Horse paths), review its diff, then proceed sequentially through the list above. Dispatch one agent at a time, not in parallel — that's the whole point of this breakdown (keep each agent's context small and focused, and let the user/reviewer catch drift before it compounds).

## Occupation tier-list CSV

Not part of this rewrite's scope, but noting it exists: `feast-for-odin/.research/Occupations Tier List for Norwegians.csv` and `feast-for-odin/.campaign/` (committed, powers the `#campaign` tab per `feast-for-odin/CLAUDE.md`) — unrelated to the sections being touched here, don't confuse with `.research/` scratch.
