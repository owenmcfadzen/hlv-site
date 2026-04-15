# HLV Google Slides — Design Token Specification

> Build specification for translating the HLV website design system to Google Slides templates. Source: `src/design-tokens.json`, `src/styles/global.css`, and the website patterns as of 2026-04-14. Use this doc to construct a reusable Google Slides template deck tomorrow.

---

## 2.1 Slide Dimensions & Grid

| Setting | Value |
| --- | --- |
| Aspect ratio | 16:9 |
| Slide size | 25.4 cm × 14.29 cm (10 in × 5.625 in) |
| Margins (outer safe area) | 1.27 cm on all sides |
| Content grid | 12 columns × 6 rows |
| Column gutter | 0.5 cm |
| Baseline for text blocks | 24 pt (approx. 0.85 cm) |

**Assumption:** Use Google Slides → File → Page setup → Widescreen 16:9 (default). Don't use 4:3.

**Guide rulers to set up** (Slides → View → Guides → Edit guides):
- Vertical: 1.27, 3.18, 5.08, 6.99, 8.89, 10.80, 12.70 (column centers)
- Horizontal: 1.27, 4.44, 7.62, 10.80, 12.70 (row centers, with the top 1.27–3 reserved for the slide label)

---

## 2.2 Color Palette (Slides hex)

Paste these hex values directly into the Google Slides custom color picker. Save them to the theme so they appear at the top of every color dropdown.

```
Violet 600   #7B4FDB   Primary accent, section marks, cross-track
Blue 600     #3B7DD8   CTAs, links, GTM track
Coral 600    #E46C41   Energy, Product track
Pop 400      #FFD43B   Highlights (ALWAYS use dark text on this)
Green 400    #34C759   Business track
Navy 800     #182D53   Text, dark backgrounds, authority
Warm White   #FAF9F7   Slide background default
Subtle       #F0EEE8   Alternate background, photo placeholders
Dark         #18181B   Dark slides (deeper than navy — use for full-dark layouts)
Border       #E2E0DC   Dividers, 1pt strokes
Text mid     #4A5568   Secondary body
Text light   #7A8599   Captions, labels
```

**Rules carried from web:**
- Violet and blue **never adjacent** in highlighted-text blocks — contrast too low.
- Pop (yellow) — **always** dark text, never white.
- On dark backgrounds, navy drops out of the A5c signature (it IS the background).

---

## 2.3 Typography Mapping

Google Slides has Barlow as a Google Font. Load via Insert → Text → More fonts → search "Barlow", "Barlow Semi Condensed", "Literata". Set each as a theme font.

| Element | Font | Weight | Size (pt) | Color | Line height |
| --- | --- | --- | --- | --- | --- |
| Slide title (H1) | Barlow | 600 | 36 | Navy | 1.15 |
| Slide subtitle | Barlow | 400 | 18 | Text mid | 1.4 |
| Section label (above title) | Barlow Semi Condensed | 600 | 10 | Track color | 1, letter-spacing 0.08em, UPPERCASE |
| Body | Barlow | 400 | 14 | Text mid | 1.6 |
| Body lead (first sentence) | Barlow | 500 | 14 | Navy | 1.6 |
| Large number (stat) | Barlow | 600 | 72 | Navy | 0.9 |
| Stat label | Barlow Semi Condensed | 600 | 10 | Text light | 1, UPPERCASE |
| Quote | Literata Italic | 400 | 20 | Navy | 1.5 |
| Quote attribution | Barlow Semi Condensed | 500 | 10 | Text light | UPPERCASE |
| Highlighted-text block | Barlow | 600 | 44 | White (or Navy on Pop) | 1.1, padding 6pt 16pt |
| CTA button text | Barlow | 600 | 13 | White/Navy | — |

**Fallback if Barlow is blocked:** Use Roboto Condensed for labels, Roboto for body/titles, and Noto Serif Italic for quotes. Document the fallback in slide notes.

**Rules:**
- 600 is the ceiling for headings.
- Literata ONLY for blockquote slides. Don't use it in titles, captions, or UI.
- Lead sentences: weight 500 + navy color. Never bold.

---

## 2.4 Slide Layout Templates

Each layout maps to a web section pattern. Build them as Slide Masters
(Slide → Edit theme → add layout). Numbers cross-reference the live patterns
on https://hlv-site-production.up.railway.app and `/dev/lookbook` §1.6.

### 1 · Title slide (full dark) — *maps to HeroVideo overlay*
- Background: Dark `#18181B` with optional video poster image cropped behind.
- Content card: warm-white rectangle bottom-left, 60% width, 1pt border,
  subtle drop shadow. Card sits over a 1pt rule that aligns with the
  slide edge so it visually "hangs" off the dark area below.
- Three-line typographic headline in navy (Barlow 600, 44pt), staircased
  with 0 / 24 / 8 pt left-indents on lines 1–3. **Two of the three lines
  carry a colored highlight block:** line 2 in coral (white text), line 3
  in pop yellow (navy text). Don't use violet for both — vary the palette.
- Eyebrow in violet Barlow Semi Condensed, dot indicator + label.
- Two CTAs: btn-dark + secondary text-link.
- A5c bar at slide bottom (4pt tall, 6:5:4:3:2:2 widths).

### 2 · "What this is" content slide — *maps to PremiseDark*
- Background: Dark `#18181B`, white text.
- Two-column layout: text 65% / spec-table 35%, large gap.
- Left: violet eyebrow, 36pt Barlow 600 headline, 14pt body in
  rgba(255,255,255,0.72). First sentence in white weight 500 (lead pattern).
- Right: spec-table — one row per fact, 1pt rules between rows,
  Barlow Semi Condensed 10pt UPPERCASE labels (color: rgba(255,255,255,0.5)),
  Barlow 14pt values in white.
- Optional `→` text-link below the body copy.

### 3 · Section divider — *unchanged from v1*
- Warm white. 6×48pt colored bar (section mark) + 36pt section title +
  optional 14pt subtitle. Minimal.

### 4 · Full-bleed photo with overlay caption
- Photo fills slide. Bottom 50% gradient (transparent → rgba(0,0,0,0.7)).
- Overlay anchored 1.27cm from bottom-left: small Pop label, 36pt title,
  14pt subtitle. White text.

### 5 · 3-column tracks/outcomes — *unchanged*
- Three equal columns, 0.5cm gutters. Optional ghost number (42pt, 12% navy)
  above each column.

### 6 · Asymmetric "intent" CTA — *maps to Intent CTA pattern*
- Background: Dark `#18181B`. Two-column layout:
  - Left 2/3: highlighted-text stack (violet → pop), copy paragraph,
    btn-light primary + secondary white-on-dark text-link.
  - Right 1/3: 2×3 photo grid. Place 3 image cells in zigzag — (1,1), (2,2),
    (1,3). Other 3 cells stay transparent (dark slide bg shows through).
- A5c bar **omitted** here (sparingly rule applies).

### 7 · Quote slide — *unchanged*
- Two short accent bars above (Violet 28pt × 4pt + Pop 16pt × 4pt).
- Literata Italic 20pt centered. Attribution in Barlow Semi Condensed
  10pt UPPERCASE.

### 8 · Stats / numbers slide — *unchanged*

### 9 · Timeline / process — *unchanged*

### 10 · 3×3 specialties grid — *new, maps to SpecialtiesGrid*
- 3×3 bordered grid (1pt rules in `#E2E0DC`) on warm white.
- **Top 2 rows (6 cells = foundational):** 44×44pt navy icon square with
  white Carbon-style icon. Title in navy Barlow 600 20pt. Sub-label in
  Barlow Semi Condensed 11pt UPPERCASE text-light. Body in 14pt text-mid.
- **Bottom row (3 cells = optional specialties):** 44×44pt **track-colored**
  icon square (coral / green / blue) with white icon. Title in the
  matching track color. Small "Optional specialty" tag at top + arrow
  indicator (signals clickability on web; on slides, just visual cue).
- Section header above (mark + 32pt title + 14pt subtitle).

### 11 · Cities — alternating rows — *maps to CityLocations*
- For each city: full-width row split 50/50 photo + content.
- Photo side: full-bleed image cell.
- Content side: small color-tag label, 36pt title, dates in Barlow Semi
  Condensed 11pt, 16pt body with lead-sentence emphasis, meta pills,
  text-link CTA.
- Alternating direction every other slide (or every other row if shown
  multi-up): NYC photo-left, Lisbon photo-right, etc. Edge bar (6pt × full
  height, track color) sits centered on the 50% gridline (offset -3pt).

### 12 · Trust close — *maps to Care section*
- Warm white, narrow column (max 720pt wide).
- 3-bar mark above (violet + pop + coral, 5×20pt each).
- 26pt headline ("We know what you're trusting us with."), 15pt body.
- Below: 5–6 collapsed Q rows (label + plus sign), with one expanded as
  example. On slides, don't try to make these interactive — render one
  expanded, others collapsed for the visual.
- Closing block: 96×96pt portrait placeholder + signature line +
  navy SVG flourish.

### 13 · CTA / closing slide
- Reuse template 1 (Title slide) with CTA-focused copy.

## 2.5 Reusable Elements (construct as grouped Slides shapes)

### Arrow-square mark
Build in Slides:
1. Rectangle, 28pt × 28pt, fill `#FFD43B`, no stroke, 1pt corner radius.
2. Inside: a horizontal arrow shape — line 11pt wide, 2.5pt stroke, Navy, square ends, with a right-pointing chevron also Navy, stroke 2.5pt square.
3. Group (Ctrl/Cmd+G).
4. Save as "HLV arrow-square" in theme assets.

### Section mark
- Rectangle 6pt × 48pt, track color, no stroke.
- Place to the left of section titles at 20pt distance.

### A5c bar
Build as 6 rectangles, no gap between them, total height 4pt, total width = slide width (25.4cm). Widths proportional to the signature:
```
violet  : 6  → 6.35 cm
blue    : 5  → 5.29 cm
coral   : 4  → 4.24 cm
pop     : 3  → 3.18 cm
green   : 2  → 2.12 cm
navy    : 2  → 2.12 cm
```
Group as "HLV A5c bar". Usage: above title slide, above closing slide, never between every slide.

### Highlighted-text block
- Rectangle with 1pt corner radius, fill = color from palette.
- Text: Barlow 600, 44pt, white (or Navy on Pop).
- Padding: 6pt vertical, 16pt horizontal.
- When stacking three, offset horizontally: 0 / +24pt / +8pt (creates the signature staircase).

### Icons (Carbon style)
Google Slides doesn't ship IBM Carbon icons natively. Options:
1. **Recommended:** Paste SVG icons from carbondesignicons.com as grouped Slides shapes. Stroke 1.5pt, square caps, miter joins, 24pt box.
2. **Fallback:** Google Material Icons (Insert → Special characters → Material icons), outlined style, 24pt. Acceptable but less sharp.

### Ghost numbers (for process steps)
- Text box, Barlow 600, 48pt.
- Color: `#E2E0DC` (border gray).
- Opacity: 100% on the gray itself (no Slides opacity slider needed — the gray already reads as ghost).

---

## 2.6 Speaker-notes conventions
- Include the web page name this layout maps to at the top of speaker notes (e.g. `Maps to: /admissions split-hero pattern`).
- If a slide uses a non-standard color combination, note it (helps future edits stay in-palette).

## 2.7 Export / sharing
- Export PDF at "Best for printing" for client decks.
- For partner decks (co-branded), duplicate the theme, swap Violet 600 for partner primary, keep Pop and Navy fixed.

## 2.8 What NOT to do (carried from web rules)
- Don't use rounded corners larger than 2pt anywhere (the 1pt on rectangles is the rule, not a suggestion).
- Don't put violet and blue adjacent in highlighted stacks.
- Don't use Literata outside a quote slide.
- Don't put the A5c bar on every slide — it dilutes the signature.
- Don't mix icon styles. Carbon only (or Material as fallback, but pick one and stick with it).

---

*Spec version 1.1 — 2026-04-15. Updated to reflect the new HeroVideo white-card pattern, PremiseDark spec-table layout, asymmetric Intent CTA, 3×3 SpecialtiesGrid (foundational + optional with inverted icon treatment), CityLocations alternating rows, and the Care trust-close. Single-color highlighted-text stack is no longer the default — vary across coral/pop/violet.*
