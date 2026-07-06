Reference guide for the game Sunless Sea

## Structure

Tabs: Ports, Bestiary, Items, Officers, Gameplay, Lore — defined in a `TABS` array, each with a `render` function.

Data lives in JS constants: `PORTS`, `BESTIARY`, `ITEMS`, `OFFICERS`, `GAMEPLAY`, `LORE` — all fed into a `DATA` object.

Cards are rendered by `renderGrouped()` (ports/bestiary/items/officers), `renderGameplay()`, or `renderLore()`. Clicking a card opens a modal — content dispatched by `tabId` in `modalContent()`.

Images come from the Sunless Sea Gamepedia CDN via `img("hash/filename.png")` e.g. `img("3/3e/SS_claymansmall.png")`.

## Key details

- Zee toggle: ports/bestiary entries can have `zee:"under"` to show only when the underzee filter is active
- Active tab persisted in URL as `?tab=lore`
- CSS uses the shared Lantern token set (`--panel`, `--ink`, `--fjord`, `--bronze`, etc — see `.claude/lantern-theme.md`) plus a guide-local `--rust`/`--rust-bright` accent for bestiary "boss" tags
- Lore tab has a live search bar and 3-column layout, groups hardcoded into columns by entry count
- No build step — edit the file directly and reload in browser to test