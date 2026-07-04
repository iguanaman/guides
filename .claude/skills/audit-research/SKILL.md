---
name: audit-research
description: Audit a guide's distilled research .md files against its built guide HTML — verify each source's useful insight made it in, and report what's missing or intentionally excluded. Use when user says "audit research", "check research coverage", or "did we use all the research" for a given guide.
---

# Audit Research

Verify a guide's `.research/*.md` files (written by `guide-research-distiller`, see new-guide skill step 3) were actually mined into the guide's HTML.

## Argument

{guide} = guide subfolder slug (e.g. `balatro`). If not given, ask.

Verify `{guide}/.research/` exists and has `.md` files (besides `_sources.md`). If missing/empty, tell user — nothing to audit.

## What counts as useful info

Per `guide-research-finder`/`guide-research-distiller`: transferable strategy insight — why/when/tradeoffs behind a play/build/approach, notable individual-source insight, general tips/tricks. NOT reference data, stats, card/rule text, or anything findable in-game/manual (see root `CLAUDE.md` Purpose). A distilled file already filtered to this bar — treat its content as presumptively useful unless it's clearly reference-only.

## Loop

List `{guide}/.research/*.md` excluding `_sources.md`. For each file, sequentially — one `general-purpose` agent per file, wait for it to finish before dispatching the next (same rationale as new-guide's sequential distill: avoid burning the session-message limit on a parallel fan-out).

Dispatch prompt gives the agent:
- `{guide}/.research/{file}` path to read
- `{guide}/index.html` (or guide's actual HTML filename) path to read/grep itself
- Task: go through the research file's claims/entries methodically (one by one, not batched), check whether each made it into the guide (in substance — paraphrase/reorganization is fine, doesn't need verbatim match). For each one NOT found: judge whether it should be in the guide per the "useful info" bar above. Report back:
  - Included: brief confirmation, no detail needed
  - Missing but should be added: what, and where in the guide it'd fit
  - Missing on purpose (out of scope, redundant with existing content, reference-only, etc): what, and why
- Agent reports findings as its final message, doesn't edit the guide

## After all files done

Summarize to user: per-file one-liners rolled up, then a consolidated list of "should add" items (grouped by section/topic) and "intentionally excluded" items. Don't dump every agent's raw report — synthesize.

Do not edit the guide HTML during this skill — audit + report only. If user wants additions made after reviewing, that's a separate follow-up.
