# Lantern Theme

Shared design system for every guide in this repo. Apply verbatim — palette, type, nav, toggle — do not reinvent per guide. Reference impl: `feast-for-odin/index.html`.

## Token block (drop into `<style>`, top of file)

```css
/* Lantern palette — light (celadon) is home; dark = abyss teal & brass */
:root{
  color-scheme:light;
  --void:#eceadf;
  --panel:#f6f4ea;
  --panel-raised:#dfdecb;
  --ink:#2b2a20;
  --ink-dim:#65644f;
  --oxide:#9c4326;
  --oxide-bright:#b0522f;
  --bronze:#8f6212;
  --bronze-bright:#6f4c0e;
  --fjord:#2e5f58;
  --fjord-bright:#356e66;
  --line:#d2ceb8;
  --line-bright:#a9a488;
  --shadow:rgba(60,60,30,.14);
  --glow:radial-gradient(100% 55% at 50% -8%, rgba(255,253,240,.85), transparent 62%);
  --nav-bg:rgba(236,234,223,.92);
  --overlay:rgba(50,48,30,.5);
  --f-label:"Trebuchet MS","Segoe UI",Verdana,sans-serif;
}
@media (prefers-color-scheme: dark){
  :root{
    color-scheme:dark;
    --void:#0c181d; --panel:#12262f; --panel-raised:#17313c;
    --ink:#ecdfc5; --ink-dim:#b4ac92;
    --oxide:#b35538; --oxide-bright:#d4714b;
    --bronze:#d99b3c; --bronze-bright:#f0bf6b;
    --fjord:#5a8f86; --fjord-bright:#82b8af;
    --line:#1f3d44; --line-bright:#2e5860;
    --shadow:rgba(0,0,0,.5);
    --glow:radial-gradient(100% 55% at 50% -8%, rgba(30,80,95,.5), transparent 62%);
    --nav-bg:rgba(12,24,29,.92);
    --overlay:rgba(4,10,12,.8);
  }
}
:root[data-theme="light"]{
  color-scheme:light;
  --void:#eceadf; --panel:#f6f4ea; --panel-raised:#dfdecb;
  --ink:#2b2a20; --ink-dim:#65644f;
  --oxide:#9c4326; --oxide-bright:#b0522f;
  --bronze:#8f6212; --bronze-bright:#6f4c0e;
  --fjord:#2e5f58; --fjord-bright:#356e66;
  --line:#d2ceb8; --line-bright:#a9a488;
  --shadow:rgba(60,60,30,.14);
  --glow:radial-gradient(100% 55% at 50% -8%, rgba(255,253,240,.85), transparent 62%);
  --nav-bg:rgba(236,234,223,.92);
  --overlay:rgba(50,48,30,.5);
}
:root[data-theme="dark"]{
  color-scheme:dark;
  --void:#0c181d; --panel:#12262f; --panel-raised:#17313c;
  --ink:#ecdfc5; --ink-dim:#b4ac92;
  --oxide:#b35538; --oxide-bright:#d4714b;
  --bronze:#d99b3c; --bronze-bright:#f0bf6b;
  --fjord:#5a8f86; --fjord-bright:#82b8af;
  --line:#1f3d44; --line-bright:#2e5860;
  --shadow:rgba(0,0,0,.5);
  --glow:radial-gradient(100% 55% at 50% -8%, rgba(30,80,95,.5), transparent 62%);
  --nav-bg:rgba(12,24,29,.92);
  --overlay:rgba(4,10,12,.8);
}
```

Light is default (no media query needed for OS dark preference → dark applies automatically; `data-theme` attr on `<html>` overrides both ways).

## Token usage

- `--void` page background, `--panel`/`--panel-raised` cards/raised surfaces, `--ink`/`--ink-dim` text
- `--oxide`/`--oxide-bright` warm accent (danger/highlight), `--bronze`/`--bronze-bright` headings + active states, `--fjord`/`--fjord-bright` cool accent (kicker, links, focus ring)
- `--line`/`--line-bright` borders, `--shadow` box-shadows, `--overlay` modal backdrop, `--nav-bg` sticky nav background (needs alpha for `backdrop-filter:blur`)
- `--glow` body background-image (radial wash, top of page)
- No raw hex/rgba anywhere outside this token block — every color reference goes through a `var()`. Includes `body::selection`, scrollbar-thumb colors, gradient stops — all must reference tokens, not literals.

## Body + globals

```css
*{box-sizing:border-box}
html{font-size:18px}
body{
  margin:0;min-height:100vh;
  background-color:var(--void);
  background-image:var(--glow);
  background-attachment:fixed;
  background-repeat:no-repeat;
  color:var(--ink);
  font-family:"Iowan Old Style","Palatino Linotype",Palatino,"Book Antiqua",Georgia,serif;
  line-height:1.66;
  -webkit-font-smoothing:antialiased;
}
::selection{background:var(--bronze);color:var(--void)}
:focus-visible{outline:2px solid var(--fjord-bright);outline-offset:2px}
h1,h2,h3{
  font-family:inherit;
  font-variant:small-caps;
  font-weight:700;
  color:var(--bronze-bright);
  letter-spacing:.03em;
}
```

## Header + toggle

Header: kicker (uppercase label, `--f-label`, `--fjord-bright`) + `h1` (small-caps, `text-shadow:0 2px 0 var(--shadow)`) + subtitle `p` (`--ink-dim`, `max-width:52ch`).

Toggle: circular button, top-right of header, `position:absolute`. Icon via `::before` content, flips with theme:

```css
.theme-toggle{
  position:absolute;top:1.4rem;right:1.2rem;
  width:38px;height:38px;border-radius:50%;
  border:1px solid var(--line-bright);background:var(--panel);color:var(--bronze);
  cursor:pointer;font-size:1rem;line-height:1;
  display:flex;align-items:center;justify-content:center;
  transition:transform .15s ease, border-color .15s ease;
}
.theme-toggle:hover{transform:rotate(15deg);border-color:var(--bronze)}
.theme-toggle::before{content:"☾"}
@media (prefers-color-scheme: dark){ .theme-toggle::before{content:"☀︎"} }
:root[data-theme="dark"] .theme-toggle::before{content:"☀︎"}
:root[data-theme="light"] .theme-toggle::before{content:"☾"}
```

Markup: `<button class="theme-toggle" id="theme-toggle" aria-label="Toggle light/dark theme"></button>` inside the header, sibling to h1/kicker/subtitle.

Mobile (`@media(max-width:640px)`): shrink to `top:1.1rem;right:.9rem;width:34px;height:34px`.

## Toggle JS

```js
(function(){
  const root = document.documentElement;
  const saved = localStorage.getItem('guides-theme');
  if(saved === 'light' || saved === 'dark') root.dataset.theme = saved;
  function currentTheme(){
    return root.dataset.theme ||
      (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
  }
  document.getElementById('theme-toggle').addEventListener('click', () => {
    const next = currentTheme() === 'dark' ? 'light' : 'dark';
    root.dataset.theme = next;
    localStorage.setItem('guides-theme', next);
  });
})();
```

`localStorage` key `guides-theme` shared across all guides — one toggle choice should feel consistent site-wide even though each guide is a separate page/load.

## Tab nav (Atlas style — open underline, not pill buttons)

```css
nav.tabs{
  position:sticky;top:0;z-index:10;
  display:flex;flex-wrap:nowrap;justify-content:flex-start;gap:0;
  padding:0 1rem;
  background:var(--nav-bg);backdrop-filter:blur(6px);
  border-bottom:1px solid var(--line-bright);
  overflow-x:auto;overflow-y:hidden;scroll-behavior:smooth;
  -webkit-overflow-scrolling:touch;scrollbar-width:thin;
  scrollbar-color:var(--line-bright) transparent;
}
@media(min-width:900px){nav.tabs{justify-content:center}}
nav.tabs::-webkit-scrollbar{height:4px}
nav.tabs::-webkit-scrollbar-track{background:transparent}
nav.tabs::-webkit-scrollbar-thumb{background:var(--line-bright);border-radius:2px}
nav.tabs::-webkit-scrollbar-thumb:hover{background:var(--fjord)}
nav.tabs button{
  font-family:var(--f-label);font-size:.84rem;font-weight:700;letter-spacing:.05em;
  color:var(--ink-dim);background:none;border:none;
  border-bottom:2px solid transparent;padding:.7rem 1rem;
  cursor:pointer;transition:color .15s;flex:0 0 auto;white-space:nowrap;
}
nav.tabs button:hover{color:var(--ink)}
nav.tabs button:focus-visible{outline-offset:-2px}
nav.tabs button.active{color:var(--bronze-bright);border-bottom-color:var(--bronze)}
```

Guides with a different nav class name (`nav.section-nav`, etc) — restyle in place, don't rename the class (JS/markup elsewhere may depend on it). Just point the same rules at the existing selector.

## Modal (full-bleed on mobile, sticky header)

```css
.modal-overlay{
  display:none;position:fixed;inset:0;background:var(--overlay);
  z-index:100;align-items:center;justify-content:center;padding:2rem;
}
.modal-overlay.active{display:flex}
.modal{
  background:var(--panel-raised);border:1px solid var(--line-bright);border-radius:.6rem;
  max-width:720px;width:100%;height:92vh;overflow:hidden;
  display:flex;flex-direction:column;
  box-shadow:0 20px 60px var(--shadow);position:relative;
}
#modal-body{flex:1;overflow-y:auto;padding:0 2.75rem 2.5rem}
#modal-body > :first-child:not(h3){margin-top:2rem}
.modal h3{
  position:sticky;top:0;z-index:1;margin:0 0 .6rem;
  padding:2rem 3rem .8rem 0;font-size:1.6rem;
  background:var(--panel-raised);border-bottom:1px solid var(--line);
}
.modal-close{
  position:absolute;top:1.25rem;right:1.5rem;z-index:2;
  background:none;border:none;color:var(--ink-dim);
  font-size:1.4rem;cursor:pointer;line-height:1;
}
.modal-close:hover{color:var(--ink)}
```

Mobile (`@media(max-width:640px)`):

```css
.modal-overlay{padding:0}
.modal{max-width:none;height:100vh;height:100dvh;border:none;border-radius:0}
#modal-body{padding:0 1.1rem 1.6rem}
.modal h3{padding:1.4rem 2.6rem .7rem 0;font-size:1.35rem}
.modal-close{top:.9rem;right:.8rem}
```

Title (`h3`) + close button stay fixed; only `#modal-body` scrolls. On mobile the modal fills the viewport — no border/radius, no wasted edge space.

## Responsive baseline

```css
@media (max-width:640px){
  html{font-size:17px}
  header.site{padding:1.7rem 3.2rem 1rem 1rem;text-align:left}
  header.site h1{font-size:1.7rem}
  header.site .kicker{font-size:.64rem;letter-spacing:.24em;margin-bottom:.4rem}
  header.site p{margin:0;max-width:none}
  .theme-toggle{top:1.1rem;right:.9rem;width:34px;height:34px}
  nav.tabs{padding:0 .5rem}
  nav.tabs button{padding:.65rem .7rem;font-size:.8rem}
  main{padding:1.5rem 1rem 4rem}
}
@media (prefers-reduced-motion: reduce){
  .theme-toggle,.card,.action-card,nav.tabs button{transition:none}
  .theme-toggle:hover{transform:none}
}
```

Merge into each guide's existing responsive block rather than duplicating — adapt selectors to that guide's actual class names for cards/tips/etc.

## Card art (SVG icons on `.card`)

Root `index.html`'s game cards and `feast-for-odin/index.html`'s Strategy Path/Artisan Shed cards use a `.card-art` div (72-88px tall, border-bottom) before `.card-title`/`.card-body`, holding a self-contained flat-vector `<svg viewBox="0 0 400 120">` (or narrower, e.g. `200 72`) — inline gradients/shapes, no external assets, not theme-token-driven (fixed hex fills, doesn't react to light/dark toggle).
Two-sided items (e.g. artisan shed tiles) → `.card-art.card-art-split` (flex, two `viewBox="0 0 100 72"` SVGs at 50% width each) instead of one wide SVG.
New guide adding icon cards → follow this pattern for consistency; write new SVGs per icon, don't reuse another guide's.

## Porting an existing guide

1. Replace `:root` token block with the one above verbatim.
2. Rename every guide-specific var to the Lantern names (`--ink-soft`→`--ink-dim`, `--paper`→`--void`, etc) throughout the file — check for the OLD var names after, not just the `:root` block.
3. Find every raw hex/rgba OUTSIDE `:root` (body gradient stops, scrollbar-thumb rgba, modal overlay rgba, hardcoded active-tab text color, badge/seal colors) and replace with the matching token or a token-derived value. This is the step most likely to be incomplete — grep the whole file for `#[0-9a-fA-F]{3,6}` and `rgba(` after the pass and confirm zero hits outside the `:root` block.
4. Apply header kicker + `.theme-toggle` button + JS block.
5. Restyle the tab nav to the Atlas open-underline look (keep existing class name/JS).
6. If a modal exists, apply the sticky-header/full-bleed-mobile modal CSS.
7. Merge the responsive/reduced-motion rules into the guide's existing `@media` blocks.
8. Guide-specific components (board grids, seal badges, character cards, etc) keep their layout — only their colors route through tokens. Don't redesign them.
9. `sunless-sea` renders nav/modal from JS template literals, not static HTML — the CSS pass still works (classes are the same), but check template strings for inline `style="color:#..."` too.
