# Prime Fleet Care — Brand & Project Reference
> Claude Code reads this file at the start of every session. Update it when brand decisions change.

---

## Project
- **Site:** https://primefleetcare.com.au
- **Repo:** GitHub → GitHub Pages (auto-deploys on push, ~60s build time)
- **Stack:** Static HTML / CSS — multi-page site (index, faqs, privacy, reviews)
- **Deploy:** `git add -A && git commit -m "msg" && git push`

---

## Brand Colours

| Role           | Hex       | RGB           | Use                                                              |
|----------------|-----------|---------------|-----------------------------------------------------------------|
| Safety Orange  | `#D94B00` | 217, 75, 0    | Action + brand: CTAs, buttons, logo, nav rule, heading highlights (`.accent`) |
| Orange (hover) | `#B83E00` | 184, 62, 0    | Hover/pressed state of orange buttons                           |
| Amber (accent) | `#F5871F` | 245, 135, 31  | Supporting accents: section tags/eyebrows, line icons, tick marks, review stars, compliance & insurance cues |
| Amber (hover)  | `#D5720F` | 213, 114, 15  | Hover state if amber is ever used on a control                  |
| Matte Black    | `#18181A` | 24, 24, 26    | Dark backgrounds, primary sections                              |
| Cream          | `#F5F0EB` | 245, 240, 235 | Off-white sections, light content areas                         |
| White          | `#FFFFFF` | 255, 255, 255 | Clean white where needed                                        |

**Critical rules:**
- Two warm accents ONLY — Safety Orange `#D94B00` and Amber `#F5871F`. NEVER introduce blue, green, or any other hue.
- Keep their roles distinct: **orange = action/brand** (CTAs, buttons, logo, nav underline, `.accent` heading highlights, mobile call bar); **amber = supporting detail** (eyebrows/section tags, all line icons, tick marks, review stars, compliance + insurance). Do NOT use amber on buttons/CTAs.
- NEVER use pure `#000000` — always `#18181A`.
- Current production orange is `#D94B00` (a mellow safety orange). The earlier brighter `#F04E00` / `#FF6A00` are superseded — do not reintroduce them, and keep `--orange` consistent across index, faqs, privacy, and reviews.

```css
:root {
  --orange: #D94B00;      /* action + brand */
  --orange-dark: #B83E00; /* orange hover */
  --amber: #F5871F;       /* supporting accent */
  --amber-dark: #D5720F;  /* amber hover */
  --black:  #18181A;
  --cream:  #F5F0EB;
  --white:  #FFFFFF;
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
The site uses a **dark-primary** design: matte black hero, mellow safety-orange action colour, amber supporting accents, cream/white content sections.

```css
/* Hero / nav / dark sections */
.hero, nav, .dark-section  { background: #18181A; color: #FFFFFF; }
/* Orange rule under nav (use the token, not a hard-coded hex) */
nav                         { border-bottom: 2px solid var(--orange); }
/* CTA buttons (orange = action) */
.btn-primary                { background: #D94B00; color: #FFFFFF; }
.btn-secondary              { border: 1px solid #FFFFFF; color: #FFFFFF; background: transparent; }
/* Orange accent on key words */
.accent                     { color: #D94B00; }
/* Amber accent — eyebrows, icons, ticks, stars, compliance */
.accent-amber               { color: #F5871F; }
/* Stats strip */
.stats-strip                { background: #3A3A3C; }
.stat-number                { color: #D94B00; }
/* Cream/light content sections */
.light-section              { background: #F5F0EB; color: #18181A; }
/* Body text in dark sections */
.dark-section p             { color: rgba(255,255,255,0.72); }
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
| `horiz_black.png` / `horiz_orange.png` / `horiz_white.png` | Horizontal lockups |

### Badge → `/assets/brand/badge/`
`badge_orange_on_black.png` (dark bg), `badge_black_on_orange.png` (light bg), `badge_orange_on_black.svg` (vector).

### Favicon & Icons → site root `/`
`favicon.ico`, `favicon_32.png`, `favicon_16.png`, `apple-touch-icon_180.png`.

### App Icons → `/assets/brand/app-icons/` · Social → `/assets/brand/social/`

---

## Rules for Claude Code

1. Read this file **before** any changes.
2. Two warm accents only: Safety Orange **`#D94B00`** (action/brand) and Amber **`#F5871F`** (supporting accents). No other hues; amber is never used on buttons/CTAs.
3. Primary dark is **`#18181A`** — never `#000` or `#000000`.
4. This site is **dark-primary** — hero and nav are dark, CTAs are orange, accents are amber.
5. Keep `--orange`/`--amber` identical across every page (index, faqs, privacy, reviews). Reference the CSS token — never hard-code the hex in a rule.
6. Logo height in nav: 40–50px tall. Never below 36px. All favicon files sit in site root `/`.
7. Verify **WCAG AA contrast** (4.5:1) before committing any CSS.
8. Always show a **diff and local preview** before committing.
9. Commit message format: `"Brand: [short description]"`
10. After push: GitHub Pages builds in ~60s. Confirm build.

---

## UI / UX Rules — Keep it Clean

1. **Spacing over clutter** — generous padding (min 60px vertical) between sections.
2. **One primary CTA per section** — one clear orange button; don't add competing CTAs.
3. **Max 3 colours per section** — `#18181A`, an accent (`#D94B00` or `#F5871F`), and either `#F5F0EB` or `#FFFFFF`. Never mix cream and white in the same section.
4. **Type hierarchy** — H1 (Big Shoulders 700, 48–72px) → H2 (32–42px) → Body (Work Sans 400, 16px / 1.7). Never skip levels.
5. **No decorative fonts** — Big Shoulders Display and Work Sans only. No italics on headings.
6. **Button shape** — `border-radius: 100px` (pill) for all primary buttons.
7. **Icon style** — simple line icons only (Lucide/Feather). Line icons are amber.
8. **Image treatment** — hero images get a dark overlay (`rgba(24,24,26,0.55)`) so white text passes WCAG AA.
9. **Mobile-first** — all sections single-column below 640px. No horizontal scroll.
10. **No transitions > 300ms** — snappy, not sluggish.

---

## Change Log

| Date       | Change                                                                              |
|------------|--------------------------------------------------------------------------------------|
| 2026-08-24 | **Amber accent `#F5871F` added** as a two-tone warm system (orange = action, amber = supporting accents/icons/stars/compliance), applied across index, faqs, privacy, reviews. Homepage: enhanced eco card to **bunding + wastewater capture & disposal**; subtle **"fully insured — public liability"** cues; **"biggest fleet-washing challenge"** dropdown on the booking form; top-right nav with **Reviews**. Recorded current production orange as **`#D94B00`** (mellow) and standardised the nav underline + faqs/privacy to it (they were still on the old `#F04E00`). |
| 2026-06-10 | v2 — app icons & social avatars regen from master badge; Operations Manager added to Harry's sig; business card & letterhead templates; UI rules added |
| 2026-06-09 | PREMIUM UPGRADE — original bright `#F04E00` orange (since softened to `#D94B00`), wordmark with rule, vector badge, dark website, business card, email sig, letterhead |
