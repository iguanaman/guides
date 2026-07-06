---
name: new-guide
description: Scaffold a new single-file HTML reference guide in this repo (design, subfolder+index card, sourced research, layout proposal). Use when user says "new guide on {topic}" or "add a guide for {topic}".
---

# New Guide

Run steps 1-4 in order. Stop after step 4 for user input — do not write guide HTML content yet.

## 1. Design

Use the shared Lantern theme — read `.claude/lantern-theme.md` and apply its token block, type, header/toggle, nav, and modal CSS verbatim. Every guide shares one visual identity; do not invent a per-topic palette.

## 2. Scaffold

- New subfolder: `{topic-slug}/`
- Base `index.html` inside it: doctype, head, Lantern `<style>` block (tokens, globals, header/toggle, nav, modal, responsive) per `.claude/lantern-theme.md`, minimal empty-shell layout (no content yet)
- Add the toggle JS block and header markup (kicker + h1 + subtitle + `.theme-toggle` button)
- Add a card to root `index.html` linking to it (match existing card markup/style), keep the grid alphabetical by guide title
- New subfolder gets its own `CLAUDE.md` (empty/minimal placeholder — filled in once guide structure is known)
- Add the new guide to the `## Guides` list in root `CLAUDE.md`

## 3. Research (find sources, then distill each sequentially)

Ensure `{topic-slug}/.research/` is gitignored (add/confirm entry in root `.gitignore`, create the file if it doesn't exist).

- Dispatch `guide-research-finder` with {topic} and `{topic-slug}`. It writes `{topic-slug}/.research/_sources.md` (table: `slug | title | url | note`) and returns the same rows inline.
- For each row in `_sources.md`, dispatch `guide-research-distiller` one at a time, sequentially — wait for each to finish before dispatching the next. Pass {topic}, `{topic-slug}`, the row's `slug` as `{source-slug}` (verbatim — it's the output filename), and the row's url. Distiller reads its one source and writes `{topic-slug}/.research/{source-slug}.md` before ending its turn. Sequential avoids burning the session-message limit on a parallel fan-out that dies mid-batch.
- Don't pass file-naming/splitting/organization instructions in these dispatch prompts — each distiller owns exactly one source → one file; that scheme lives in `guide-research-distiller.md`, not the dispatch prompt.
- After all distillers run, diff the finder's source list against the written `.md` files; re-run any source that produced no file (session limit, fetch block, etc).

## 4. Propose layout

After research lands, read the distilled `.md` files and propose to the user (plain chat, not brainstorming-skill, not formal plan mode):

- Recommended sections/tabs for the guide, driven by what {topic} actually needs (not modeled on other guides in this repo)
- What strategy/insight content goes in each section (not reference data — see root CLAUDE.md Purpose)
- Whichever layout pattern fits {topic} best — card-grid, tables, accordion, etc — chosen independently per guide

End with an open question for the user's go-ahead or changes. Do not start writing the guide's HTML content until they respond.
