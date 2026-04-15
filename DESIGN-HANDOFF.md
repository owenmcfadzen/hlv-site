# HLV Site — Design Handoff

> State of the redesign, single source of truth for anyone picking this up — including Cate, future Claude sessions, or another designer.

**Live:** https://hlv-site-production.up.railway.app
**Repo:** https://github.com/owenmcfadzen/hlv-site
**Stack:** Astro (static site) · Railway (deploy-on-push)
**Last design pass:** 2026-04-15

---

## 1 · What's built

### Pages (13 total, all deploy statically)
- `/` — landing page (the most iterated surface — see §3)
- `/programs` — Summer 2026 programs, four cities, comparison
- `/program/nyc`, `/program/lisbon`, `/program/porto`, `/program/seoul` — per-city deep pages
- `/alumni`, `/about`, `/team`, `/admissions`, `/parents`, `/specialties` — supporting pages
- `/dev/lookbook` — **private design reference** (not linked from nav) — every pattern in one scroll

### Landing page narrative (top to bottom)

| # | Section | Component | Purpose |
|---|---------|-----------|---------|
| 1 | Hero | `<HeroVideo />` | Video bg (placeholder: banner image) + white overlay card, bottom-left, hangs 1/3 below the video into the next section |
| 2 | "What Hudson Lab is" | `<PremiseDark />` | Dark surface receiving the hero overlay. Left: eyebrow + H2 + copy. Right: spec-sheet table. |
| 3 | Partners | `<PartnersMarquee />` | A5c color bar as top divider (dark→light bridge). Horizontal text-wordmark marquee. |
| 4 | Specialties | `<SpecialtiesGrid />` | 3×3 grid: 6 foundational topics (black icon squares) + 3 optional specialties (colored icon squares, clickable) |
| 5 | Photo pair | inline | Two studio photos |
| 6 | Quote | `<Quote />` | Alum voice, warm variant |
| 7 | Cities | `<CityLocations />` | Full-width alternating city-rows (NYC / Lisbon / Porto / Seoul) |
| 8 | Intent CTA | inline | Full-bleed dark section, 2/3 text + 1/3 photo grid (zigzag), primary apply button |
| 9 | How to Apply | inline | 3-step process, clean informational band |
| 10 | Care section | inline | Trust close: acknowledgement + accordion FAQ + signature from Cate |
| 11 | Footer | `<Footer />` | Links + A5c bar |

---

## 2 · Component inventory

### Shipped and in use

| Component | File | Used on | Notes |
|---|---|---|---|
| `HeroVideo` | `src/components/HeroVideo.astro` | landing | White overlay card, 3-line staircase headline with per-line color accent, video placeholder until `videoSrc` prop is passed |
| `PremiseDark` | `src/components/PremiseDark.astro` | landing | Dark section with spec-sheet table on the right |
| `SpecialtiesGrid` | `src/components/SpecialtiesGrid.astro` | landing | 3×3 grid, foundational vs optional cells |
| `CityLocations` | `src/components/CityLocations.astro` | landing | Full-width alternating rows. Reusable on `/programs` (future swap) |
| `PartnersMarquee` | `src/components/PartnersMarquee.astro` | landing | Optional `topBar` prop renders A5c as top divider |
| `A5cBar` | `src/components/A5cBar.astro` | hero top, Partners top, footer | `flush` prop drops the default 48px top margin |
| `FAQList` | `src/components/FAQList.astro` | (unused on landing — Care has inline) | Accordion with native `<details>/<summary>` |
| `Nav` | `src/components/Nav.astro` | every page | Fixed top nav, variants: light, dark |
| `Footer` | `src/components/Footer.astro` | every page | |
| `Quote` | `src/components/Quote.astro` | landing | warm + navy variants |
| `ArrowSquare` | `src/components/ArrowSquare.astro` | many | The HLV identity mark (pop square + navy arrow) |
| `SectionHeader` | `src/components/SectionHeader.astro` | many | mark + title + optional subtitle |
| `HeroSplit` | `src/components/HeroSplit.astro` | admissions, parents | Older split hero with edge bar |
| `StatsBar`, `IconCard`, `TravelGrid`, `WeekPlan`, `PartnerSplit`, `PhotoBreak`, `PhotoPair` | `src/components/*.astro` | various | Existing building blocks |

### Deliberately left as "available but not currently used"

- `FAQList` — `admissions.astro` and `parents.astro` use inline FAQ markup; the component is available for the next consolidation pass.
- Old `.lp-hero`, `.lp-premise`, `.tracks-section` — **removed** from `index.astro`. Git history preserves them.

---

## 3 · Design system at a glance

Full values live in `src/design-tokens.json` (source of truth). Rendered CSS in `src/styles/global.css`.

### Palette

| Name | Hex | CSS var | Role |
|---|---|---|---|
| Violet 600 | `#7B4FDB` | `--violet` | Primary identity, cross-track |
| Blue 600 | `#3B7DD8` | `--blue` | CTAs, links, GTM track |
| Coral 600 | `#E46C41` | `--coral` | Energy, Product track |
| Pop 400 | `#FFD43B` | `--pop` | Highlights — **always use dark text on pop** |
| Green 400 | `#34C759` | `--green` | Business track |
| Navy 800 | `#182D53` | `--navy` | Text, dark anchor, authority |
| Warm white | `#FAF9F7` | `--warm-white` | Default page bg |
| Subtle | `#F0EEE8` | `--bg-subtle` | Secondary bg, photo placeholders |
| Dark | `#18181B` | `--dark` | Dark sections (deeper than navy — bg only) |
| Border | `#E2E0DC` | `--border` | 1px rules |

**A5c signature:** Violet : Blue : Coral : Pop : Green : Navy in proportions 6 : 5 : 4 : 3 : 2 : 2.

### Typography

- **Primary:** Barlow (weights 400 / 500 / 600)
- **Labels:** Barlow Semi Condensed (weights 500 / 600, UPPERCASE, ~0.08em tracking)
- **Accent:** Literata Italic — **blockquotes only**
- Scale: hero 56, page 52, section 36, highlighted 48, card 22, sub 19, body 17, body-large 18, label 12, label-xs 11
- Lead-sentence pattern: weight 500 + navy color (inside regular body text)

### Radius + shape

- **1px** buttons, inputs, CTAs
- **2px** cards, containers (max)
- **0px** icons, tags, dividers, arrow-squares
- **Rule: no pills, no rounded corners beyond 2px, anywhere**

### Icons

- Carbon style (IBM Carbon Icons)
- Stroke width 1.5px
- `stroke-linecap: square`
- `stroke-linejoin: miter`
- Track-colored per context; on `SpecialtiesGrid` foundational cells icons are white on navy square

### Spacing

- Section padding: 120px top / 100–120px bottom
- Page gutter: 80px sides (desktop), 48px (tablet), 24px (mobile)
- Section-mark: 6×48px bar beside section titles
- Bordered grid gutter: 1px (single-line divisions)

### Patterns & decisions

- **A5c bar — sparingly.** Page-top afterglow (below hero), Partners section top, footer. Not between every section and not below dark CTAs.
- **Highlighted-text blocks (`hl-block`)** — designed for dark backgrounds per tokens. On the **white hero card** we allow the staircase pattern with per-line color accents (currently coral + pop) as a documented exception.
- **Editorial voice:** quiet, confident, no hype. Lead sentences emphasize. Literata sits only inside blockquotes.
- **Omotenashi** — named accountability is the smallest form. Cate signs off the landing page personally.

---

## 4 · For slide/print translation

The single most useful file for adapting this system to slides or print is **`hlv-slides-spec.md`** at repo root — it maps every palette hex, type scale, layout template, and reusable element into Google Slides / A4–A5 print terms. Keep that doc as the canonical guide.

Quick cheat sheet for non-web surfaces:

| Element | Web | Slides | Print (A4/A5) |
|---|---|---|---|
| Palette | CSS vars | Theme colors + hex | CMYK (see spec) |
| Primary type | Barlow | Barlow Google Font | Barlow embedded in PDF |
| Label type | Barlow Semi Condensed | same | same |
| Quote type | Literata Italic | same (import font) | embed |
| Arrow-square | `ArrowSquare.astro` component | grouped shape (square + line + chevron) | grouped vector |
| A5c bar | `A5cBar.astro` | 6 rectangles in 6:5:4:3:2:2 proportion, 4pt tall | same, 1mm tall |
| Section mark | 6×48px bar | 6×48pt rectangle | 2×14mm bar |
| Highlight block | hl-block class | grouped rect + text, 1pt corner radius | same |

**Rules that apply everywhere:**
- Violet and blue never adjacent in highlighted-text stacks
- Pop (yellow) always uses dark text
- Max 3 highlighted lines in a stack
- Radius rule: max 2px (or 1pt in slides, or same pt-equivalent in print)
- Barlow weight 600 is the ceiling for headings

---

## 5 · Recent decisions worth preserving

1. **Hero = value + feeling, first section = what it is.** The original hero was doing both; we split them. Hero stays emotional; PremiseDark takes on explanation.
2. **Dark cascade.** Hero overlay bottom-left → PremiseDark text top-left → spec table top-right — criss-cross geometry as the eye moves down.
3. **One dark moment per scroll region.** Originally the page had a dark hero AND a dark CTA at the bottom. Now it's Hero (video) → PremiseDark → Intent CTA → Care (quiet close). Each dark surface earns its presence.
4. **Full-bleed layouts** are worth the complexity. Intent CTA and CityLocations both abandon the centered-max-width pattern for edge-to-edge composition — gives those sections more presence on the page.
5. **Specialties section consolidated.** Was "Three Tracks" (Product/Business/GTM) on the landing. Now `SpecialtiesGrid` shows 6 foundational topics + 3 optional specialties. Product/Business/GTM live in the PremiseDark lead copy — they're specialties of their own kind, and the page has one Specialties surface, not two.
6. **FAQ accordion uses native `<details>`** — no JS, fully accessible, keyboard-navigable by default. If we need animation, CSS only.
7. **Care section replaces Parents + FAQ.** One trust surface instead of two. Signature from Cate is the omotenashi payoff.
8. **Icon hierarchy in SpecialtiesGrid.** Foundational cells: navy squares + white icons. Optional cells: colored squares (track color) + white icons + colored titles. The visual weight falls on specialties.

---

## 6 · Known gaps / next-pass candidates

- **Hero video.** Placeholder is the current site's `HLV Website Banner 2026.jpeg`. Drop a real video at `public/img/hero.mp4` and pass `videoSrc="/img/hero.mp4"` to `<HeroVideo />`.
- **Porto photo.** No Porto image available from the current Squarespace site. Provide one at `public/img/porto.webp` and wire via `photoSrc` in `CityLocations.astro`.
- **`/programs` city rows** still use inline markup. Swap to `<CityLocations showHeader={false} />` to share the component.
- **`admissions.astro` + `parents.astro`** have inline FAQ markup. Migrate to `<FAQList />` for a single FAQ style across the site.
- **Hero eyebrow alignment.** The hero eyebrow still says "Summer 2026 · Four cities · Applications open" which is good; the page flow is consistent. (Previously this was a mismatch when the Tracks section existed.)
- **Signature under Cate.** The SVG is a stylized placeholder flourish. Swap with a real signature file when available.

---

## 7 · How to continue

### Run locally
```bash
cd hlv-site
npm install
npm run dev    # http://localhost:4321
```

### Edit tokens
`src/design-tokens.json` is the source of truth. `src/styles/global.css` mirrors the tokens — update both together when a value changes.

### Add a new page
Create `src/pages/your-page.astro`, wrap in `<Base title="…">`, compose using existing components.

### Add a new component
Drop it in `src/components/`, mirror the scoped-style pattern used elsewhere, document it in `src/pages/dev/lookbook.astro` §1.6 with a real embed and a caption explaining the decision.

### Deploy
Push to `main`. Railway redeploys within ~2 minutes. No manual step.

### Where to look first if something breaks
- Layout issue → check `src/styles/global.css`
- Component-specific → scoped `<style>` block inside the component
- Cross-component visual bug → search for `!important` or `:global()` (both are used sparingly; both have broken things before)

---

## 8 · Quick links

- **Live site:** https://hlv-site-production.up.railway.app
- **Lookbook:** https://hlv-site-production.up.railway.app/dev/lookbook
- **Design tokens:** `src/design-tokens.json`
- **Global styles:** `src/styles/global.css`
- **Slides spec:** `hlv-slides-spec.md`
- **Worksheet spec:** `hlv-worksheet-spec.md`

---

*This document is the handoff. Update it when the landing page structure changes, when components are added, or when a decision worth preserving gets made. Keep it honest — list gaps, not just wins.*
