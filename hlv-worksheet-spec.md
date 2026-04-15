# HLV Printed Worksheets — Design Specification

> Specifications for A4 and A5 printed worksheets used during HLV summer programs. Built to match the HLV design system from `src/design-tokens.json`. Use this doc to generate print-ready PDFs tomorrow.

---

## 3.1 Page Setup

### A4 Worksheet (default for facilitator handouts, cohort worksheets)
| Setting | Value |
| --- | --- |
| Page size | 210 × 297 mm (portrait) |
| Margins | 15 mm top, bottom, left, right |
| Bleed | 3 mm outside trim (if print-trim) |
| Safe area | 12 mm inside trim (critical content) |
| Grid | 6-column × 10-row, 4mm gutter |
| Body text width | ≤ 160 mm (avoid full-width paragraphs) |

### A5 Worksheet (daily student handouts, reflection cards)
| Setting | Value |
| --- | --- |
| Page size | 148 × 210 mm (portrait) |
| Margins | 12 mm all sides |
| Bleed | 3 mm (if print-trim) |
| Safe area | 9 mm inside trim |
| Grid | 4-column × 8-row, 3mm gutter |

**Assumption:** Students write on worksheets with pens. Line spacing is more generous than on-screen.

---

## 3.2 Print Color Considerations

### CMYK equivalents (approximate — test-print before finalizing)
| Color | RGB/Hex | CMYK |
| --- | --- | --- |
| Violet 600 | #7B4FDB | 65 / 75 / 0 / 0 |
| Blue 600 | #3B7DD8 | 75 / 45 / 0 / 0 |
| Coral 600 | #E46C41 | 5 / 70 / 75 / 0 |
| Pop 400 | #FFD43B | 0 / 15 / 80 / 0 |
| Green 400 | #34C759 | 65 / 0 / 85 / 0 |
| Navy 800 | #182D53 | 100 / 85 / 35 / 50 |
| Warm White | #FAF9F7 | 0 / 1 / 2 / 0 (or paper stock color) |
| Subtle | #F0EEE8 | 3 / 3 / 7 / 0 |
| Border | #E2E0DC | 10 / 8 / 12 / 0 |

### Tint variants for print backgrounds (use 10% fill)
- Violet 10%: `#F2ECFB`
- Coral 10%: `#FCEDE7`
- Blue 10%: `#EBF2FB`
- Green 10%: `#EAF7EE`

### Print rules
- **Navy** prints reliably as a dark anchor. Use for all text.
- **Pop (yellow)** prints well on warm white but can look muddy on cream stock. Test first.
- **Avoid** using Pop as a large background fill — it's disruptive at worksheet scale. Use Pop only as small accent swatches (≤ 20mm).
- All decorative fills should be tinted variants (10–15% of saturated color).
- **Print stock recommendation:** 120gsm uncoated warm white. 100gsm acceptable for single-use reflection cards.

---

## 3.3 Worksheet Layouts

### Layout 1 — Title header (reusable across all worksheets)
- Top strip, 30mm tall.
- Left: small arrow-square (10mm), "HLV" wordmark in Barlow 600, 14pt.
- Right: Session name + date + cohort (Barlow Semi Condensed 9pt, UPPERCASE, Text light).
- Below: student name field — single line, 120mm wide, 9pt label "NAME" above, 0.5pt underline below.
- 1pt full-width horizontal rule to separate header from content.

### Layout 2 — Two-column workspace
- Left column (40% width): instructions or prompt in Barlow 10pt / 14pt leading. Optional: small icon top-left.
- Right column (60% width): blank workspace. Faint dot-grid at 5mm spacing in `#E2E0DC` tint, 20% opacity.
- 1pt vertical rule between columns.

### Layout 3 — Canvas / sketch area
- Full-width title field (20mm tall) with 0.5pt underline.
- Large open area (150 × 200mm on A4, 100 × 130mm on A5).
- Light grid: 5mm dot grid in `#E2E0DC` at 15% opacity.
- 0.5pt border around the area.
- Bottom-right corner: small "sketch" or "canvas" label in Barlow Semi Condensed 7pt.

### Layout 4 — Structured form (Business Model Canvas, SWOT, etc.)
- Bordered grid of cells, 1pt borders in `#E2E0DC`.
- Each cell has a header strip 8mm tall, filled with 10% tint of a track color (Violet / Coral / Blue / Green rotating).
- Cell label: Barlow Semi Condensed 9pt, UPPERCASE.
- Cell body: writing space with faint horizontal rules at 7mm spacing.

### Layout 5 — Reflection / journaling
- Prompt at top: Barlow 14pt italic (or Literata Italic 12pt for a softer tone — acceptable here).
- Below: writing lines, 8mm apart, 0.25pt stroke in `#E2E0DC`.
- Right margin: thin colored edge bar (4mm × full writing-area height) in track color for the day.
- Footer line: "Date ___________" in Barlow Semi Condensed 8pt UPPERCASE.

### Layout 6 — Comparison matrix
- 4–6 row table.
- Column headers: Barlow Semi Condensed 9pt UPPERCASE on 10% tinted backgrounds (one track color per column).
- Row labels: Barlow 10pt Navy, left-aligned.
- Cell body: writing space with 0.25pt border all around.
- Recommended row heights: 18mm on A4, 14mm on A5.

### Layout 7 — Timeline planner (weekly)
- Horizontal 7-column grid (Mon–Sun).
- Column headers: day name in Barlow Semi Condensed 9pt UPPERCASE, date below in Barlow 10pt.
- Each column: 40mm tall writing area, faint horizontal rules at 8mm.
- Top bar colored in rotating A5c order (Violet / Blue / Coral / Pop / Green / Navy / + repeat).

### Layout 8 — Presentation prep (slide-by-slide outline)
- 6 boxes per A4 page (2 × 3), each 80 × 65mm.
- Each box represents one slide.
- Box header: "SLIDE 01" etc. in Barlow Semi Condensed 8pt.
- Box body: blank with 0.5pt border. Dot-grid background at 5mm.

---

## 3.4 Typography for Print

Print typography differs from screen — tighter leading, slightly smaller labels, crisper weights.

| Element | Font | Weight | Size | Leading | Use |
| --- | --- | --- | --- | --- | --- |
| Page title | Barlow | 600 | 20pt | 24pt | Top of worksheet |
| Section heading | Barlow | 600 | 14pt | 18pt | Within a worksheet |
| Subheading | Barlow | 600 | 11pt | 15pt | Sub-sections |
| Body | Barlow | 400 | 10pt | 14pt | Instructions, prompts |
| Body small | Barlow | 400 | 9pt | 13pt | Secondary notes |
| Label | Barlow Semi Condensed | 600 | 8pt | 10pt, UPPERCASE, 0.08em tracking | All labels, field headers |
| Field label (form) | Barlow Semi Condensed | 500 | 9pt | 11pt, Text light color | Name, date, etc. |
| Reflection quote | Literata Italic | 400 | 12pt | 17pt | Reflection prompts only |
| Footer | Barlow Semi Condensed | 500 | 7pt | 9pt, Text light | Page numbers, meta |

### PDF export settings
- Embed all fonts.
- Output intent: ISO Coated v2 (CMYK) for print houses, or sRGB for digital distribution.
- Flatten transparency (some tints use 10% alpha — flatten on export).
- Export PDF/X-1a for press, PDF/A for archival.

---

## 3.5 Reusable Print Elements

### Arrow-square (print version)
- 10mm × 10mm square, Pop Pantone or CMYK equivalent.
- Navy arrow inside, stroke 0.75mm.
- Used in header and as a corner accent on cover sheets.

### Section mark
- 2mm × 14mm vertical bar, track color.
- Placed 5mm left of section headings.

### A5c bar (print)
- 1mm tall, full content width (180mm on A4, 124mm on A5).
- Six colored segments matching the signature proportions (6:5:4:3:2:2).
- Use once per worksheet, typically above footer.

### Field underlines
- 0.25pt stroke in `#7A8599` (Text light).
- Length depends on expected content: 60mm for name, 40mm for date, full column width for notes.

### Dot grid
- Dots at 5mm spacing, 0.5mm diameter, `#E2E0DC` at 20% opacity.
- Use for canvas / sketch / brainstorming areas.

---

## 3.6 Printing Checklist

Before sending to print:
- [ ] All fonts embedded in the PDF.
- [ ] Bleed set to 3mm if trim required.
- [ ] CMYK conversion completed (no RGB warnings in preflight).
- [ ] Pop yellow tested on the actual paper stock.
- [ ] Worksheet title matches the session plan.
- [ ] Student name field included.
- [ ] Page number in footer (for multi-page sets).
- [ ] Version stamp in footer (e.g. `v1.0 · 2026-06-15`).
- [ ] Test print at actual size, not fit-to-page.

---

## 3.7 Binding & distribution

- **Stapled booklets:** A5 daily worksheets, 16–24 pages, saddle-stitched.
- **Loose handouts:** A4, punched for 3-ring or Japanese binding (Japanese stab binding works well with the tonal palette).
- **Covers:** Use dark navy covers with Pop arrow-square bottom-right and A5c bar at top edge.

---

*Spec version 1.0 — 2026-04-14. Owen to approve CMYK conversions and test-print before first session distribution.*
