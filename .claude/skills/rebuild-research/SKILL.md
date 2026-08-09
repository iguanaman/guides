---
name: rebuild-research
description: Re-distill every existing .research/*.md file for a guide from its original source URL, using the current guide-research-distiller agent — for when the distiller's instructions have changed and old files need regenerating. Use when user says "/rebuild-research {guide}" or "rebuild the research files for {guide}".
---

# Rebuild Research

Argument {guide} = subfolder slug (e.g. `feast-for-odin`). Accept fuzzy/spaced input (e.g. "fields of arle" → `fields-of-arle`) — match against existing subfolders. If ambiguous or no match, ask.

Verify `{guide}/.research/` exists with `.md` files besides `_sources.md`. If missing/empty, tell user — nothing to rebuild.

## 1. Extract source URLs

For each `.md` file in `{guide}/.research/` (excluding `_sources.md`):
- Grep the file for a line starting `Source:` (or, if absent, read just the first ~10 lines) to find its source URL — don't read the whole file.
- Record filename (minus `.md` = the `{source-slug}`) → URL pairs.
- If a file has no discoverable URL, flag it and skip — don't guess.

## 2. Delete existing files

Delete every `.research/*.md` file being rebuilt (not `_sources.md`) before dispatching any agent — the distiller checks whether its output file already exists and skips rewriting if so, so stale files must be gone first.

## 3. Dispatch guide-research-distiller in parallel batches

Batches of 6 — 6 Agent calls in one message, wait for the batch, then send the next 6 (same rationale as `new-guide` step 3: a dead batch costs 6 re-runs, not the whole list).

Each dispatch prompt passes: {topic} (guide's proper name, not slug), `{topic-slug}` = {guide}, the recorded `{source-slug}`, and the source URL. Instruct it to fetch and distill per its own instructions into `{guide}/.research/{source-slug}.md`.

## 4. Verify

After all dispatches complete, list `{guide}/.research/*.md` and confirm every extracted slug has a corresponding file. Re-run any that produced none (fetch block, session limit, etc) — report blocks the distiller surfaced instead of retrying blindly.

## 5. Report

Summarize: files rebuilt, any skipped (no URL found), any still blocked with the distiller's reported reason.
