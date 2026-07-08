---
name: rewrite-research
description: Rewrite an existing guide's content sections from its refreshed .research/*.md files, discarding existing prose. Use when user says "/rewrite-research {guide}", "rewrite the research", or "redo {guide} content from research".
---

# Rewrite Research

Argument {guide} = subfolder slug (e.g. `feast-for-odin`). If not given, ask.

Verify `{guide}/.research/` exists with `.md` files besides `_sources.md`. If missing/empty, tell user — nothing to rewrite from.

Load the `write-guide-content` skill before any writing step — governs collation rules, voice, no-source-meta, no-walkthroughs.

## 1. Map sections

Read `{guide}/index.html` structure (grep `<section id=`, `<h2>`, `<h3>` — don't read the whole file if large). Read `{guide}/.research/_sources.md` and skim each `.md` filename for topic.

For each tab/section, classify:
- **Rewrite candidate** — backed by strategy/insight research, not pure reference.
- **Fact-list, preserve as-is** — card lists, stat tables, anything reference/rulebook-derived (matches root `CLAUDE.md` Purpose: not a reference mirror).
- **Locked/out of scope** — guide's own `CLAUDE.md` marks it locked, or it's non-research-driven (CSV-driven tabs, personal house-rule tabs, setup/rules tabs).

Read `{guide}/CLAUDE.md` for guide-specific locks/exclusions before finalizing.

## 2. Plan agent breakdown per rewrite-candidate section

For each section, decide granularity:
- Single coherent topic, few sources → one agent.
- Section already contains multiple sub-topics each with their own dedicated research file(s) (e.g. per-animal, per-island-tier, per-path) → split into multiple agents, one per sub-topic or small sub-topic cluster.
- Group small/related sub-topics into one agent dispatch rather than one-agent-per-card; split out sub-topics with many dedicated sources of their own.

Map each planned agent to: target section/subsection in the HTML, and the specific `.research/*.md` filenames it should read (by filename, not "all of them").

## 3. Confirm scope with user

Present: which tabs/sections are in scope, which are fact-list-preserved, which are excluded and why, and the planned agent count/breakdown (section → research files). Ask for corrections before dispatching anything. Do not start step 4 until user confirms.

## 4. Dispatch agents sequentially

One `general-purpose` agent at a time — wait for each to finish before dispatching the next (same rationale as `new-guide`/`audit-research`: avoid burning the session-message limit on a parallel fan-out).

Each dispatch prompt includes:
- Guide path, target section (HTML id/line range), and exact `.research/*.md` filenames to read (only those — not the whole `.research/` folder).
- Instruction to load and follow the `write-guide-content` skill.
- Instruction to ignore the section's existing HTML content entirely when deciding what to write — do not read it for ideas, carry over phrasing, or preserve claims not present in the assigned research files. The only exception: markup structure/classes needed to match the guide's existing layout (card grid, tab-panel, etc) — copy structure, not prose.
- Instruction to write directly into `{guide}/index.html`, replacing the target section's content in place.
- Solo-perspective + all-expansions framing if that's the guide's stated scope (check guide's `CLAUDE.md`).

After each agent finishes, briefly report what changed before moving to the next dispatch.

## 5. Wrap-up

After all agents complete, summarize sections rewritten vs preserved vs skipped. Do not run `audit-research` automatically — that's a separate follow-up if the user wants verification.
