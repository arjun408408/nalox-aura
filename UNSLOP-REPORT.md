# Nalox Aura website — unslop redesign report

Redesign of `index.html` following the **unslop** skill by Damir Sokolovsky
([@heydamir](https://x.com/heydamir), https://github.com/heydamir/unslop, CC BY 4.0).
Commit `8ca726b` on `main`, GitHub Pages build confirmed on that commit.

Process note: the skill's step 4 says show the audit and direction and wait.
Arjun's instruction for this task was to redesign it properly and do
everything, so the work proceeded without the pause and is documented here
instead.

## Audit — slop signs found in the old page

The old page hit most of the skill's tell list, several of them everywhere:

- **Aurora background** — three large radial colour washes fixed behind the
  whole page, plus a faint grid overlay and three blurred `.orb` blobs
  drifting on an infinite 16 s loop.
- **Too many tints of one hue** — body text alone used ~7 near-identical
  blues (`#9db4dd`, `#6f87b3`, `#bcd6ff`, `#cfe4ff`, `#dceaff`, `#eaf3ff`…)
  with no text-role system; surfaces came from stacked translucent blues.
- **Gradient text** — logo wordmark, the hero headline's second line, the
  PRO side block; the hero's red line also carried a red text-shadow glow.
- **Colored glows everywhere** — blue shadows on buttons and the logo tile,
  a red glow on the PRO card, glow dots on the pill badge, glowing step
  numbers, a soft blue shadow under the panel mock.
- **Glassmorphism as the default surface** — translucent cards with
  `backdrop-filter: blur(14px)`; feature cards also had a radial hover-glow
  layer (`.fcard::before` — the layer that once swallowed every download
  click on this page).
- **Gradient buttons and logo tile** — blue linear-gradient buttons, a
  red-pink gradient for PRO, a gradient sparkle tile for the logo.
- **Emoji as the icon system** — every feature card, download meta line,
  tutorial heading and most buttons used emoji (⬇ 📩 📸 🔤 🎞️ 🤖 📦 🔐…).
- **Loud display type** — Sora at weight 800 for headings, uppercase
  kickers tracked out at .22em, all-caps tags ("NEW", "BIG LIBRARY",
  "PRO") in glowing pills.
- **Off-scale spacing and radii** — section padding like `78px 0 10px`,
  radii mixed 9/11/12/14/18/20/24/999 px with no system.
- **Layout tells** — everything centred and stacked; the hero carried
  **three** CTAs (download + features + a ghost Instagram button) under a
  pulsing-dot pill badge; 15 feature cards in one uniform 3-column grid of
  identical cards; glowing meta pills under the download buttons.
- **Motion tells** — infinite floaty/pulse/drift loops, hover lifts
  (`translateY(-5px)`), catch-all `transition:.25s` / `.3s`.

## Direction

- **Product** — a free Windows panel for After Effects, Premiere Pro and
  DaVinci Resolve that puts a working editor's whole toolkit in one place.
- **Character** — exact, workmanlike, quietly confident.
- **World** — the editing suite after dark: timeline rulers, keyframe
  diamonds, the ink-dark chrome of the host apps themselves.
- **Moments** — (1) the hero panel preview, rebuilt in code in the ink
  palette: one solid accent tab, one quiet red PRO tab, no glow; (2) the
  real `Preview.mp4` in the tutorial section, framed plainly.
- **Signature** — a timeline-ruler tick strip under every section heading
  (hairline ticks, one accent playhead tick), with version and size figures
  set in mono. Nothing else on the page competes with it.

## The system

- **Ink ramp** (tinted neutrals): bg `#0b0d14`, surface `#11141c`, raised
  `#1a1e28`, raised-2 `#232836`; hairlines at 8% / 16% white.
- **Text roles (3)**: `#eef0f5` primary, `#a3a9b8` secondary, `#7a8296` muted.
- **One accent**: the product's own blue, solid — button fill `#1e64d8`
  (white text, 5.42:1), accent text `#6ea8ff` (~8:1 on bg).
- **Red means PRO only**: `#ff5c77` for PRO marks/text, `#d92c47` solid for
  PRO buttons (white text, 4.77:1). One semantic green `#4cc38a` for the
  PRO checklist ticks. No other hues.
- **Type**: Inter 400/500/600 (Sora removed) + IBM Plex Mono for figures,
  versions and kickers; Noto Sans Devanagari stays in the stack for Hindi.
  Hierarchy by size; headings weight 500.
- **Spacing**: 4 px scale throughout — sections 96 px, grid gaps 16,
  card padding 24, radii 16 (cards) / 10 (buttons, icon boxes, steps).
- **Icons**: one inline SVG sprite, stroke 1.5, `currentColor` — 20 px in
  icon boxes, 18 px in tutorial headings, 16 px in buttons. Logo redrawn
  as a flat ring with a filled core.
- **Motion**: one easing `cubic-bezier(.22,1,.36,1)`; scroll reveal toned
  to opacity + 8 px rise over .45 s; hovers step border/surface only;
  buttons press at scale .98. All loops removed.

## What changed, per pass

1. **Spacing** — every padding/margin/gap moved onto the 4 px scale;
   section rhythm unified (96 px top, headings and leads on shared gaps);
   radii rationalised (16/12/10/8 by nesting).
2. **Color** — aurora washes, orbs and grid overlay deleted; the blue-tint
   pile replaced by the Ink ramp + 3 text roles; blue kept as one solid
   accent; red quarantined to PRO; gradients and glows removed everywhere
   (the only gradient left is the ruler's neutral repeating tick pattern).
3. **Icons** — all emoji replaced by the single SVG line set, one weight,
   sized by context; the ✓ checklist glyph (a text character, not an
   emoji) kept in the product's green.
4. **Copy** — emoji stripped from all button/label strings (EN + HI);
   headlines end without a period; tags sentence-cased ("New", "Big
   library"); PRO section retitled "Everything included. One PRO upgrade".
   No claim changed: still free download, PRO by DM with a Machine Code,
   no price anywhere, Premiere's no-tracking honesty intact, DaVinci still
   framed as a companion helper, no AE claims on other editions' cards.
5. **Type** — Sora 800 → Inter 500/600; uppercase tracked kickers → 12 px
   mono sentence case; version/size figures in IBM Plex Mono.
6. **Layout** — hero becomes a split: copy left, panel preview right; the
   hero's third CTA (ghost Instagram button) removed — one primary, one
   secondary; the pulsing pill badge became a plain mono eyebrow line;
   the Clipping feature card spans two columns so the grid has rhythm;
   section headers left-aligned on the content column.
7. **Details** — focus-visible rings on interactive elements; `::selection`
   in the accent; scrollbar restyled to the ink ramp; meta lines ("Windows
   · After Effects 2020+ · ~21 MB") set in mono instead of glowing pills.
8. **Visuals** — no stock or generated imagery needed: the hero visual is
   the product preview rebuilt in code (the honest choice for a panel —
   it shows the actual UI vocabulary), and the tutorial keeps the real
   `Preview.mp4`. No image prompt was required.
9. **Motion** — drift/floaty/pulse keyframes deleted; one easing curve;
   transitions name their properties; nothing moves on a loop.

## Invariants verified after the redesign

- **EN/HI pairs**: 204/204 balanced (was 205/205; the −1 is the hero's
  removed third CTA, both languages). A scripted diff against the old file
  confirms the only string changes are the copy-pass edits listed above.
- **Download hrefs byte-identical** to the old page (AE ×1, Premiere ×1,
  DaVinci ×2 including the #davinci section).
- **JSON-LD block byte-identical**; Google verification meta and
  `googlefa89e8da465c0218.html` untouched; "Made by Nalox" kept; contact
  still Instagram DM @nalox_ff + YouTube @naloxff only; zero occurrences
  of "mnyintelligence"; no Muse/Meta branding; `update.json`, releases
  and extension code untouched.
- **Language toggle tested** in headless Chrome: EN → HI → EN all render
  correctly (Devanagari in Noto Sans Devanagari).

## Download click test (live)

- GitHub Pages build for commit `8ca726b`: **built**. The live page bytes
  are identical to the committed file (`cmp` clean).
- Real mouse clicks (headless Chrome, live page markup): for each of the
  four download anchors, `elementFromPoint` at the button's centre returns
  the button itself — no overlay intercepts — and the click fires a
  request to the exact release-asset URL. (The sandbox VM's Chrome cannot
  tunnel HTTPS through its egress proxy — even example.com fails — so the
  click's request was captured at the network layer and the payload was
  verified separately by direct download.)
- Downloaded byte sizes from the live URLs, exact match:
  - After Effects `nalox-aura-v7.1.2.zip` — **21,745,228 B**
  - Premiere Pro `nalox-aura-premiere-v1.zip` — **21,128,734 B**
  - DaVinci Resolve `nalox-aura-davinci-v1.1.zip` — **166,701 B**

## Credit

Design system and audit method: **unslop** by Damir Sokolovsky
(@heydamir) — https://github.com/heydamir/unslop — CC BY 4.0.
Credited discreetly in the page footer and in an HTML comment in
`index.html`, as the license asks.
