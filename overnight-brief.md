# Overnight Build Brief — HLV Design System Craft + Slides Prep

## Context
You're working on the HLV website at `/home/claude/hlv-site` (or clone from `github.com/owenmcfadzen/hlv-site`). The site has 12 pages and 16 components built in Astro. The design system is documented in `src/design-tokens.json` and the skill at `/mnt/skills/user/hlv-site/SKILL.md`.

**Read the skill file first.** It has the full color palette, typography rules, radius rules, icon conventions, and page patterns.

**Owen is asleep. Do not ask questions. Make decisions and document them. Push to GitHub when done.**

## GitHub Push

```bash
cd /home/claude/hlv-site
git remote set-url origin https://<TOKEN>@github.com/owenmcfadzen/hlv-site.git
```

Owen will provide the token. If no token is available, save all work locally and document what was built.

---

## Task 1: Visual Exploration Page (`/dev/lookbook`)

Create `src/pages/dev/lookbook.astro` — a private reference page showing every component variation and new visual patterns Owen can explore. This is NOT a public page. It's a design tool.

### Structure the lookbook in sections:

**1.1 Hero Variations (show 5-6 options)**
- Typographic hero (current: landing, alumni) — show with different headline sizes, mark positions
- Split hero (current: admissions, parents) — show left/right, with/without edge bar, different edge colors
- Dark hero with highlighted text blocks (current: city programs) — show the violet→pop→navy sequence, try coral→pop→navy, blue→pop→navy
- Full-bleed photo hero with overlay text — new pattern, hasn't been explored yet
- Centered hero — headline centered, subtext centered, minimal (good for mission/about pages)
- Video placeholder hero — dark bg with centered play button and caption

**1.2 Geometric Patterns & Visual Elements**

The HLV identity mark is the arrow-square (36px yellow pop square with navy arrow). Explore:
- Arrow-square at different scales (24px, 36px, 48px, 64px)
- Arrow-square as a repeating pattern / texture
- The A5c color bar as a vertical element (not just horizontal)
- Section mark variations: the 6×48px colored bar, but also try 6×24px, a dot instead of a bar, a square instead of a bar
- Diagonal cut sections (subtle 2-3deg angle on section dividers)
- Colored edge bars on cards/containers (like the photo edge bars but on bordered cards)
- Gradient overlays using the A5c palette on dark sections
- Corner accents — small geometric marks in card corners (think: the arrow square as a corner treatment)

**1.3 Section Pattern Variations**

For each, show 2-3 visual treatments:

- **Bordered grid**: current 2×2 and 3×2. Try 4×1 (horizontal strip), 1×4 (vertical stack), and asymmetric (1 large + 2 small)
- **Stats bar**: current horizontal. Try vertical sidebar stat column, circular stat badges, large number + small label stacked
- **Quote section**: current warm/navy. Try pull-quote (large text inline), sidebar quote (narrow column), quote with photo of speaker
- **Card layouts**: current flat bordered. Try cards with colored top-edge, cards with icon-left/text-right (horizontal), cards with large ghost numbers, cards with photo backgrounds
- **Timeline/process**: current numbered steps. Try connected dot timeline, horizontal stepper, kanban-style columns
- **Photo layouts**: current full-width and pair. Try 3-up grid, masonry 2-col, photo with overlapping text card, circular crop with caption
- **CTA sections**: current text-left/button-right. Try centered with highlight blocks, dark band with stats, split CTA (two paths: student vs parent)

**1.4 Color & Typography Specimens**

Show:
- All 6 A5c colors as large swatches with hex, RGB, CSS var
- Text on each color background (test contrast)
- The full type scale: h1 through body, labels, lead sentences
- Lead sentence treatment comparison: 500 weight vs bold vs color only
- Literata italic in context (blockquotes only — show why it only works there)

**1.5 Button & Interactive Element Variations**

- btn-dark, btn-violet, btn-light, btn-outline — all at standard and small
- Arrow-square button (current)
- Text links with arrow
- Tag/badge styles (like the day-tag on program pages)
- Toggle/tab patterns for future interactive elements

### Technical requirements:
- Single Astro page, all content visible by scrolling
- Each section has a clear label and separator
- Use `<style>` block for any new patterns
- Any pattern worth keeping should be extracted to a component and noted in comments
- Mobile responsive is NOT required for this page — it's a desktop reference

---

## Task 2: Google Slides Design Token Export

Create `/home/claude/hlv-slides-spec.md` — a complete specification document that can be used tomorrow to build Google Slides templates matching the HLV design system.

### Include:

**2.1 Slide dimensions & grid**
- Recommended: 16:9 (25.4cm × 14.29cm)
- Margin: 1.27cm all sides
- Content grid: 12-column, 0.5cm gutter

**2.2 Color mapping for slides**
Map each HLV color to its Google Slides hex:
```
Violet 600: #7B4FDB — Primary accent, section markers
Blue 600: #3B7DD8 — CTAs, links, GTM track
Coral 600: #E46C41 — Energy, Product track
Pop 400: #FFD43B — Highlights (dark text only)
Green 400: #34C759 — Business track
Navy 800: #182D53 — Text, dark backgrounds
Warm White: #FAF9F7 — Slide background default
Subtle: #F0EEE8 — Alternate background
Dark: #18181B — Dark slides
```

**2.3 Typography mapping**
Google Slides doesn't have Barlow by default. Document:
- Primary: Barlow (available as Google Font in Slides)
- Fallback: Roboto (native)
- Slide title: Barlow 600, 36pt, Navy
- Slide subtitle: Barlow 400, 18pt, text-mid
- Body: Barlow 400, 14pt, line-height 1.6
- Labels: Barlow Semi Condensed 600, 10pt, uppercase, tracked
- Quote: Literata Italic 400, 20pt

**2.4 Slide layout templates (describe 10-12)**
Each layout should map to a web section pattern:
1. Title slide — dark bg, highlighted text blocks, A5c bar at bottom
2. Section divider — colored mark + title, minimal
3. Content + photo — split layout (text left, photo right)
4. Full-bleed photo with overlay caption
5. 3-column content (like tracks or outcomes)
6. 2-column comparison
7. Quote slide — Literata italic, accent marks
8. Stats/numbers slide — large numbers, small labels
9. Timeline/process — horizontal steps
10. Bordered grid — 2×2 or 3×2 content blocks
11. Icon + text rows — like the safety or logistics sections
12. CTA / closing slide — dark bg, A5c bar

**2.5 Reusable elements for slides**
- Arrow-square mark (describe exact construction in Slides: grouped rectangle + line)
- Section mark (6×48px bar — describe as Slides shape)
- A5c bar (describe as grouped rectangles with proportional widths)
- Carbon-style icons (note: use Google Material icons as closest fallback in Slides, or embed SVGs)

---

## Task 3: Worksheet Design Spec

Create `/home/claude/hlv-worksheet-spec.md` — specifications for A4 and A5 printed worksheets.

### Include:

**3.1 Page setup**
- A4: 210 × 297mm, 15mm margins
- A5: 148 × 210mm, 12mm margins
- Bleed: 3mm if printing with trim

**3.2 Print color considerations**
- Navy (#182D53) prints well on standard paper
- Pop (#FFD43B) needs care — test on cream paper
- Use 10% tint variants for background fills in print
- All colors need CMYK equivalents (provide these)

**3.3 Worksheet layouts (describe 6-8)**
1. Title header (logo, session name, date, student name field)
2. Two-column workspace (instructions left, workspace right)
3. Canvas/sketch area (large open space with light grid)
4. Structured form (fields for business model canvas, SWOT, etc.)
5. Reflection/journaling (lined area with prompt)
6. Comparison matrix (grid for evaluating options)
7. Timeline planner (weekly view for project milestones)
8. Presentation prep (slide-by-slide outline boxes)

**3.4 Typography for print**
- Barlow exports well to PDF
- Body: 10pt / 14pt leading
- Headings: Barlow 600, 14pt
- Labels: Barlow Semi Condensed 600, 8pt, uppercase
- Field labels: 9pt, text-light color

---

## Constraints

1. **No external API calls** — no Make, Notion, Loops, Tally, Stripe. Web-only.
2. **No Chrome browser interaction** — this runs in terminal only.
3. **No questions** — make reasonable decisions and document assumptions.
4. **Push to GitHub** when each major task is complete, not just at the end.
5. **Read `/mnt/skills/user/hlv-site/SKILL.md` before starting.**
6. **Build the lookbook first** — it's the highest-value deliverable.
7. **Test build (`npx astro build`) before every push.**

## Success Criteria

Owen wakes up to:
- A `/dev/lookbook` page he can scroll through showing every visual variation
- A slides spec document he can use immediately in Google Slides
- A worksheet spec document he can use for print layout
- Everything pushed to GitHub and deployed to Railway

---

## Task 4: Cost & Aid Page (`/cost-aid`)

Create `src/pages/cost-aid.astro` — a dedicated pricing and financial aid page. Audience is primarily parents. Tone: transparent, respectful, adult-to-adult. No sales language.

**Read the skill file first for design system rules.**

### Page structure:

**4.1 Hero (light, no photo)**
- Label: "Cost & Financial Aid"
- Headline: "Transparent Pricing. Real Financial Aid."
- Subtext: lead sentence style. "Tuition ranges from $3,000 to $6,500 depending on location and enrollment type. Financial aid is available and need-based. Here's everything you need to know."

**4.2 Program Pricing Comparison (bordered-grid)**
Clean comparison grid, 5 columns (label + 4 cities):

| | NYC | Lisbon | Porto | Seoul |
|---|---|---|---|---|
| Residential | $6,500 | $3,000 | $3,000 | $6,000 |
| Day Student | $3,500 | — | — | $4,000 |
| Deposit | 10% | 10% | 10% | 10% |

Below the grid, a note: "Tuition covers all sessions, materials, expert facilitation, daily lunch, city activities, and lifetime alumni network access."

**4.3 What's Included vs What's Not (two-column layout)**

Included (with check icons, blue):
- All program sessions and materials
- Expert facilitation (small group ratio)
- Daily lunch
- City activities and cultural programming
- Alumni network access (lifetime)
- Supervised housing (residential programs)
- On-site support staff

Not included (with neutral icons):
- Travel to/from program city
- Dinner (curated restaurant guides provided)
- Personal spending money
- Travel insurance (recommended)
- Group flight (optional, priced separately)

**4.4 Financial Aid (full-width, accent-note style with green border)**

Prose section:
- "We believe cost should never be the reason a qualified student can't participate."
- Need-based, families under ~$100K income eligible
- No separate application — indicate interest on enrollment form
- Both tuition AND housing support available
- Aid recipients participate fully, no distinction
- Application fee waivers available for qualifying families
- "If cost is a concern, reach out before applying. We'll give you a straight answer."

**4.5 Referral & Friends (two bordered cards side by side)**

Card 1 — Alumni Referral:
- Referrer: $250 cash OR $500 tuition credit if returning
- Referee: $250 off tuition
- "Share your name as your referral code"

Card 2 — Friends Enrollment:
- Two friends apply and enroll together
- Each receives 10% tuition credit (up to $250)
- "Apply with a friend. Both save."

Note below: "Referral and friends credits cannot be combined with each other or other promotional discounts."

**4.6 Payment & Refund Policy (clean FAQ-style or timeline)**

Items to cover:
- Application fee: $45 (before Feb 28) / $60 (after March 1). Fee waivers available.
- Deposit: 10% of tuition, non-refundable, secures your place
- Full payment: due May 31 for students accepted before May 15. Within 5 days for later acceptances.
- Payment methods: credit card (2.75% convenience fee), check, wire transfer
- Refund: full tuition minus deposit if cancelled before May 1 ($100 processing fee). After May 1, non-refundable.
- Credit card fee waived on application fee and deposit

**4.7 Regional Pricing Note**
Brief section explaining:
- EU and Portuguese students may be eligible for ecosystem-supported tuition through local partnerships
- Portuguese students enroll directly through Unicorn Factory Lisboa
- Contact hello@hudsonlabventures.com for regional pricing details

**4.8 CTA**
- "Questions about cost?" + email link
- "Ready to apply?" + link to /admissions

### Design notes:
- Parents page tone — warm, calm, no flash
- Use the bordered-grid pattern for the pricing comparison
- Icons from Carbon set (check marks, calendar, wallet)
- Green accent for financial aid section
- Mobile: grid collapses to scrollable horizontal table or stacked cards
- Add to nav? Probably link from Parents page and Admissions page rather than top nav

### Add navigation links:
- Parents page cost section: link to /cost-aid for "full details"
- Admissions page cost section: link to /cost-aid
- DO NOT add to main nav (keep nav clean: Program, About, Alumni, Parents, Apply)

### Meta description:
"Hudson Lab Ventures tuition ranges from $3,000 to $6,500 by location. Financial aid, referral credits, and payment plans available. Transparent pricing for families."
