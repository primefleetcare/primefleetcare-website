# Prime Fleet Care — Brand & Project Reference
> Claude Code reads this file at the start of every session. Update it when brand decisions change.

---

## Project
- **Site:** https://primefleetcare.com.au
- **Repo:** GitHub → GitHub Pages (auto-deploys on push, ~60s build time)
- **Stack:** Static HTML / CSS — single-page site
- **Deploy:** `git add -A && git commit -m "msg" && git push`

---

## Brand Colours

| Role          | Hex       | RGB           | Use                                      |
|---------------|-----------|---------------|------------------------------------------|
| Premium Orange | `#F04E00` | 240, 78, 0   | CTAs, buttons, accents, headings, rules  |
| Matte Black   | `#18181A` | 24, 24, 26   | Dark backgrounds, primary sections       |
| Cream         | `#F5F0EB` | 245, 240, 235| Off-white sections, light content areas  |
| White         | `#FFFFFF` | 255, 255, 255| Clean white where needed                 |

**Critical rules:**
- NEVER use blue, green, or any other accent — orange only.
- NEVER use pure `#000000` — always `#18181A`.
- NEVER change the orange to `#FF6A00` (old colour) or similar — it is `#F04E00`.

```css
:root {
  --color-orange: #F04E00;
  --color-black:  #18181A;
  --color-cream:  #F5F0EB;
  --color-white:  #FFFFFF;
}
```

---

## Typeface

| Font                  | Weight | Use                                   | Google Fonts                                |
|-----------------------|--------|---------------------------------------|---------------------------------------------|
| Big Shoulders Display | 700    | Logo, display headings, stats         | Big+Shoulders+Display:wght@700              |
| Work Sans             | 400,600| Body, taglines, contact, UI labels    | Work+Sans:wght@400;600                      |

**Google Fonts CDN (add to `<head>` once):**
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@700&family=Work+Sans:wght@400;600&display=swap" rel="stylesheet">
```

**CSS:**
```css
h1, h2, h3, .stat-number { font-family: 'Big Shoulders Display', sans-serif; font-weight: 700; }
body, p, a, button, input, label, li { font-family: 'Work Sans', sans-serif; }
```

---

## Website Direction — DARK PRIMARY
The site uses a **dark-primary** design: matte black hero, premium orange accents, cream/white content sections.

```css
/* Hero / nav / dark sections */
.hero, nav, .dark-section  { background: #18181A; color: #FFFFFF; }
/* Orange rule under nav */
nav                         { border-bottom: 2px solid #F04E00; }
/* CTA buttons */
.btn-primary                { background: #F04E00; color: #FFFFFF; }
.btn-secondary              { border: 1px solid #FFFFFF; color: #FFFFFF; background: transparent; }
/* Orange accent on key words */
.accent                     { color: #F04E00; }
/* Stats strip */
.stats-strip                { background: #3A3A3C; }
.stat-number                { color: #F04E00; }
/* Cream/light content sections */
.light-section              { background: #F5F0EB; color: #18181A; }
/* Body text in dark sections */
.dark-section p             { color: rgba(255,255,255,0.72); }
/* Subtle ghost watermark (hero right side) */
.hero::after { content:"PRIME"; font-family:'Big Shoulders Display',sans-serif;
               font-size: clamp(200px,25vw,340px); font-weight:700; color:rgba(255,255,255,0.035);
               position:absolute; right:5%; top:50%; transform:translateY(-50%);
               pointer-events:none; user-select:none; }
```

---

## Brand Assets (repo paths)

### Wordmark → `/assets/brand/wordmark/`
| File | Use |
|------|-----|
| `stacked_black.png`   | Light/cream backgrounds |
| `stacked_orange.png`  | Dark backgrounds ← USE IN DARK NAV |
| `stacked_white.png`   | White text on any dark bg |
| `stacked_twotone.png` | Black PRIME + orange FLEET CARE — print |
| `stacked_tagline_black.png` | With "CLEAN · CHARGE · ASSIST" tagline |
| `horiz_black.png`     | Horizontal — light bg |
| `horiz_orange.png`    | Horizontal — dark bg |
| `horiz_white.png`     | Horizontal — any dark bg |

### Badge → `/assets/brand/badge/`
| File | Use |
|------|-----|
| `badge_orange_on_black.png` | Dark backgrounds |
| `badge_black_on_orange.png` | Orange or light backgrounds |
| `badge_lineart_on_white.png`| White/light backgrounds |
| `badge_orange_on_black.svg` | Vector — for print/signage/scaling |

### Favicon & Icons → site root `/`
- `favicon.ico` — browser tab (main)
- `favicon_32.png`, `favicon_16.png`
- `apple-touch-icon_180.png`

### App Icons → `/assets/brand/app-icons/`
`appicon_1024.png`, `_512.png`, `_192.png`, `_1024_rounded.png`, `apple-touch-icon_180.png`, `maskable_512.png`

### Social → `/assets/brand/social/`
`avatar_black_1080.png`, `avatar_orange_1080.png`

---

## HTML Snippets

### `<head>` block:
```html
<!-- Fonts -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Big+Shoulders+Display:wght@700&family=Work+Sans:wght@400;600&display=swap" rel="stylesheet">
<!-- Favicon -->
<link rel="icon" href="/favicon.ico" sizes="any">
<link rel="icon" type="image/png" sizes="32x32" href="/favicon_32.png">
<link rel="icon" type="image/png" sizes="16x16" href="/favicon_16.png">
<link rel="apple-touch-icon" sizes="180x180" href="/apple-touch-icon_180.png">
<meta name="theme-color" content="#18181A">
<!-- Social share -->
<meta property="og:image" content="https://primefleetcare.com.au/assets/brand/social/avatar_black_1080.png">
<meta property="og:image:width" content="1080"><meta property="og:image:height" content="1080">
```

### Nav logo (dark nav):
```html
<a href="#" class="logo" aria-label="Prime Fleet Care">
  <img src="/assets/brand/wordmark/stacked_orange.png" alt="Prime Fleet Care" height="46">
</a>
```

---

## Rules for Claude Code

1. Read this file **before** any changes.
2. Primary orange is **`#F04E00`** — never any other orange.
3. Primary dark is **`#18181A`** — never `#000` or `#000000`.
4. This site is **dark-primary** — hero and nav are dark, CTAs are orange.
5. Logo height in nav: 40–50px tall. Never below 36px.
6. All favicon files must sit in site root `/`.
7. Verify **WCAG AA contrast** (4.5:1) before committing any CSS.
8. Always show a **diff and local preview** before committing.
9. Commit message format: `"Brand: [short description]"`
10. After push: GitHub Pages builds in ~60s. Confirm build.

---

## UI / UX Rules — Keep it Clean

These apply to every page, section and component on the site:

1. **Spacing over clutter** — generous padding (min 60px vertical) between sections. Never stack elements tightly.
2. **One primary CTA per section** — each section has one clear orange button. Don't add multiple competing CTAs.
3. **Max 3 colours per section** — use `#18181A`, `#F04E00`, and either `#F5F0EB` or `#FFFFFF`. Never mix cream and white in the same section.
4. **Type hierarchy** — H1 (Big Shoulders 700, 48–72px) → H2 (Big Shoulders 700, 32–42px) → Body (Work Sans 400, 16px / 1.7 line-height). Never skip levels.
5. **No decorative fonts** — Big Shoulders Display and Work Sans only. No italics on headings.
6. **Button shape** — `border-radius: 100px` (pill) for all primary buttons. Never square corners.
7. **Icon style** — use simple line icons only (e.g. Lucide or Feather). No filled colourful icons.
8. **Image treatment** — hero images must have a dark overlay (`rgba(24,24,26,0.55)`) so white text always passes WCAG AA.
9. **Mobile-first** — all sections must be single-column below 640px. No horizontal scroll.
10. **No transitions > 300ms** — hover and state animations must feel snappy, not sluggish.

---

## Change Log

| Date       | Change                                                                              |
|------------|--------------------------------------------------------------------------------------|
| 2026-06-10 | v2 — app icons & social avatars regen from master badge; Operations Manager added to Harry's sig; business card & letterhead HTML templates added; MORNING_GUIDE moved to root; UI rules added |
| 2026-06-09 | PREMIUM UPGRADE — #F04E00 orange, wordmark with rule, vector badge, dark website, business card, email sig, letterhead |
