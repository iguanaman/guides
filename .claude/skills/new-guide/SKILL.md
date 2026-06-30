---
name: new-guide
description: Scaffold a new single-file HTML reference guide in this repo (design, subfolder+index card, sourced research, layout proposal). Use when user says "new guide on {topic}" or "add a guide for {topic}".
---

# New Guide

Run steps 1-4 in order. Stop after step 4 for user input — do not write guide HTML content yet.

## 1. Design

If {topic}'s visual identity isn't obvious, do a quick web search (box art, official branding, fan-art mood) to ground the palette/mood before picking — don't invent a theme from nothing when reference material exists.

Auto-pick a color theme/aesthetic fitting {topic} on its own merits (palette, font pairing, mood) — do not look at other guides in this repo for style cues; each guide's design should fit its own subject, not match siblings. Use `:root` CSS vars for theming (`--panel`, `--ink`, accent colors, etc). No need to confirm with user — just pick and proceed; it can be revised later.

## 2. Scaffold

- New subfolder: `{topic-slug}/`
- Base `index.html` inside it: doctype, head, the chosen `:root` vars, minimal empty-shell layout (no content yet)
- Add a card to root `index.html` linking to it (match existing card markup/style)
- New subfolder gets its own `CLAUDE.md` (empty/minimal placeholder — filled in once guide structure is known)
- Add the new guide to the `## Guides` list in root `CLAUDE.md`

## 3. Research (find sources, then fan out distillers in parallel)

Ensure `{topic-slug}/.research/` is gitignored (add/confirm entry in root `.gitignore`, create the file if it doesn't exist).

- Dispatch `guide-research-finder` with {topic}. It returns a source list (`slug | url | note`), no files written yet.
- From that list, dispatch one `guide-research-distiller` per source, all in a single message (parallel) — each gets {topic}, `{topic-slug}`, and its own `{source-slug}` + url. Each distiller reads its one source and writes its own `.md` immediately, before ending its turn.
- Don't pass file-naming/splitting/organization instructions in these dispatch prompts — each distiller owns exactly one source → one file; that scheme lives in `guide-research-distiller.md`, not the dispatch prompt.

## 4. Propose layout

After research lands, read the distilled `.md` files and propose to the user (plain chat, not brainstorming-skill, not formal plan mode):

- Recommended sections/tabs for the guide, driven by what {topic} actually needs (not modeled on other guides in this repo)
- What strategy/insight content goes in each section (not reference data — see root CLAUDE.md Purpose)
- Whichever layout pattern fits {topic} best — card-grid, tables, accordion, etc — chosen independently per guide

End with an open question for the user's go-ahead or changes. Do not start writing the guide's HTML content until they respond.
