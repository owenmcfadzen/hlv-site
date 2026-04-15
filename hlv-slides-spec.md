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

Each layout maps to a web section pattern. Build them as Slide Masters (Slide → Edit theme → add layout).

### 1 · Title slide (full dark)
- Background: Dark `#18181B`.
- Three highlighted-text blocks, stacked vertically, offset 0 / 24pt / 8pt from left (L → R stagger).
- Color sequence: Violet → Pop → Navy (or Coral → Pop → Navy for energy, Blue → Pop → Navy for GTM).
- A5c bar at bottom, full width, 4pt tall.
- Bottom-right: small HLV arrow-square (see §2.5).

### 2 · Section divider
- Background: Warm white.
- 6×48pt colored bar (section mark) left-aligned at 1.27 cm.
- Next to it: section title 36pt Barlow 600.
- Below title: 14pt subtitle in Text mid.
- Minimal. No decoration.

### 3 · Content + photo (split)
- Two columns, 50/50.
- Left: text — section label, title, 2–3 short paragraphs.
- Right: full-bleed photo (edge to edge of right half).
- 6pt edge bar on the inside edge of the photo (track color).

### 4 · Full-bleed photo with overlay
- Photo fills entire slide.
- Dark gradient overlay, bottom 50% (linear: transparent → rgba(0,0,0,0.7)).
- Bottom-left overlay: section label in Pop, title 36pt, short subtitle. Overlay anchored 1.27cm from bottom-left.

### 5 · 3-column content
- Three equal columns, 0.5cm gutters.
- Each column: small icon OR colored top-edge (4pt), title, short paragraph.
- Use for tracks (Product / GTM / Business) or outcomes.
- Optional: ghost number (42pt, 12% navy) above each column.

### 6 · 2-column comparison
- Two columns, 50/50.
- Column headers with colored top-edge (e.g., violet vs. coral).
- Rows below with 1pt border rule (border color `#E2E0DC`).

### 7 · Quote slide
- Background: Warm white (or Navy for dramatic).
- Two short accent bars above the quote: Violet 28pt × 4pt, Pop 16pt × 4pt, 4pt gap.
- Literata Italic 20pt centered, max 12 words per line.
- Attribution below in Barlow Semi Condensed 10pt UPPERCASE, Text light.

### 8 · Stats / numbers
- Up to 4 stats in a single row.
- Each: 72pt Barlow 600 Navy number, 10pt Barlow Semi Condensed UPPERCASE label below.
- 1pt vertical divider between stats.

### 9 · Timeline / process
- Four to six horizontal steps, evenly spaced.
- Top: 1pt horizontal line connecting all steps.
- Each step: 12pt colored dot on the line, step number (01) 24pt, step title 14pt Barlow 600.
- Colors rotate: Violet → Coral → Blue → Pop (→ Green if 5 steps).

### 10 · Bordered grid (2×2 or 3×2)
- Four or six cells, separated by 1pt border (Border `#E2E0DC`).
- Each cell: 16pt padding, icon optional top-left, title 14pt Barlow 600, body 11pt text mid.
- Best for "what you'll do / what you'll get" pages.

### 11 · Icon + text rows
- Vertical stack of 3–5 rows.
- Each row: 24pt carbon-style icon left (track color), title + paragraph right.
- 1pt horizontal rule between rows.

### 12 · CTA / closing slide
- Dark background, centered content.
- Highlighted-text blocks: "Ready when" (violet) / "you are." (pop, navy text).
- Centered button: "Apply" on white with arrow-square (see §2.5).
- A5c bar at very bottom, 4pt tall.

---

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

*Spec version 1.0 — 2026-04-14. Owen to review font loading and icon strategy before first full deck build.*
