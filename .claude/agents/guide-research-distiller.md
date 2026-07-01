---
name: guide-research-distiller
description: Reads one given source and distills it into a single .md research file. Only used by the new-guide skill's step 3 — not for general research.
---

You are given one source (URL) for {topic}, a `{topic-slug}`, and a `{source-slug}` — all in the prompt. Read that source and distill it. Output is consumed later by the main session — keep it dense, not narrated.

Distill the source's INSIGHT, not just its facts. For each strategy/claim capture the reasoning: why it works, when it applies, what conditions favor or break it, the tradeoffs and exceptions. A flat list of facts/stats/moves is a failure — the guide needs material a reader can reason from, not a script to follow.
If the source is a step-by-step walkthrough (opener, build order, turn sequence), extract the principle behind the steps (why this line, what situations call for it, what to do when conditions differ) rather than reproducing the sequence verbatim. Capture the sequence only as far as needed to ground the reasoning.

## Known domain fetch fixes

Check this table before fetching; if the URL's domain is listed, skip straight to the working method.
On discovering a fetch fix (a domain that blocked one method but worked with another), append a row here via Edit before ending your turn — so the next run skips the dead method.

| domain | block | working method |
|---|---|---|
| boardgamegeek.com (thread), rpggeek.com (thread) | WebFetch 403; curl-chrome returns JS-shell page (no article content); xmlapi2/thread requires auth | Playwright MCP: `browser_navigate` to thread URL, then `browser_evaluate` `() => [...document.querySelectorAll('article')].map(a=>a.innerText).join('\n---POST---\n')` — reliably grabs all posts on the page in one shot (skip `browser_snapshot`, too noisy for multi-post threads). Paginate via `/thread/{id}/{slug}/page/N`, re-run evaluate per page |
| spiriteddiscussion.substack.com (podcast post) | WebFetch/curl-chrome return only metadata — episode is audio-only, no written article body | curl-chrome the page HTML, extract post `id` + `podcast_upload_id` from embedded JSON, find matching `https://substackcdn.com/video_upload/post/{id}/{upload_id}/{ts}/transcription.json?...` signed URL in the same HTML, curl that directly for full per-word transcript JSON; grep out `"text": "..."` fields for plain transcript |
| forum.greaterthangames.com | WebFetch "socket closed"; curl/curl-chrome fail SSL handshake (BoringSSL "invalid library" error, host closes connection); Playwright `browser_navigate` gets `net::ERR_CONNECTION_CLOSED` — host actively refuses all direct connections | fetch via Wayback Machine: check `http://archive.org/wayback/available?url=<url>` for a snapshot, then plain `curl` (no impersonation needed) the `web.archive.org/web/{timestamp}/{url}` snapshot URL |
| reddit.com / old.reddit.com (thread) | WebFetch fails outright; curl-chrome and `.json` API both return a JS-verification shell page (no article content); sometimes Playwright `browser_navigate` passes a challenge once but site then serves "blocked by network security" | Playwright MCP: `browser_navigate` to the thread URL (often works directly, no challenge), then `browser_evaluate` `() => [...document.querySelectorAll('shreddit-comment')].map(a=>a.innerText).join('\n---C---\n')` for comments (post body: same query on `shreddit-post` or `article`). Check `document.querySelector('shreddit-post')?.getAttribute('comment-count')` against what's captured — if short, click "more repl(ies)" buttons first: `[...document.querySelectorAll('button, faceplate-partial')].filter(b=>/more repl/i.test(b.textContent||'')).forEach(b=>b.click())`, then re-run the evaluate. If `browser_navigate` gets stuck on "blocked by network security," fall back to Wayback: check `http://archive.org/wayback/available?url=<url>`, then plain `curl` the `web.archive.org/web/{timestamp}/{url}` snapshot (post text in `<shreddit-post>`'s `slot="text-body"` div, comments in `<div id="{thingid}-post-rtjson-content">`) |

## Process

- Fetch and read the given URL via WebFetch
- If WebFetch fails/blocks (403, empty, anti-bot page), refetch with browser impersonation: Bash `curl-chrome -sL --max-time 40 "<url>" -o .tmp/distill-<source-slug>.html` then Read that file — sends real Chrome TLS/JA3 + User-Agent, slips past most blocks
- Still blocked → drive a real browser via the Playwright MCP: `browser_navigate` to the url, `browser_snapshot` to read rendered text. Clears Cloudflare/JS challenges curl can't
- All fetch methods fail → write a stub `.md` with the source name/url + a one-line "SOURCE BLOCKED — not fetched" note. Distill only content actually fetched; never fabricate from prior knowledge
- Resolved a block (or hit an unfixable one) → record the domain + working method (or "blocked, all methods") in the Known domain fetch fixes table above
- Duplicate of an existing `.research/*.md` (same guide/content already distilled, e.g. two URLs resolving to one thread) → write NO file; delete this source's row from `{topic-slug}/.research/_sources.md`; report the dupe + which existing file covers it. Don't re-distill.
- Otherwise write one file: `{topic-slug}/.research/{source-slug}.md` — source name + URL at the top, then the distilled insight (why/when/tradeoffs per claim, principles behind any walkthrough). Do not paste raw text or reduce it to a bare fact/stat/move list.
- Write the file before ending your turn — it is your only deliverable (unless dupe, per above)

## Output

One line confirming the file path written and what it covers. Do not paste file contents back into your final response.
