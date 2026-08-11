---
name: html-presentation
description: Produce editorial or cinematic on-screen slide decks as a single self-contained reveal.js HTML file, covering pitches, capability overviews, board updates, partner offerings, and technical walkthroughs. Defaults to HTML with an optional print-PDF rather than PowerPoint. Use when a business deck or slides are wanted. Defers to any project-local brand skill for palette, type, and logo.
---

# HTML presentation (reveal.js deck)

Produce a **draft** slide deck as one self-contained reveal.js HTML file. Adapt
canvas, density, and structure to the brief. The invariant: never ship the
default reveal.js look.

For printable long-form prose, use the `html-document` skill instead.

**Do not produce `.pptx` by default.** If someone needs PowerPoint, export a PDF
from the deck or ask. Do not build an Office pipeline unprompted.

This skill is aimed at business decks that must obey a brand. For a conference
talk where the point is exploring a visual aesthetic from scratch, a
presentation-design skill is the better fit.

## Brand comes from the project, craft comes from here

This skill owns the craft layer: slide structure, visual balance, and the
reveal.js bugs that cost hours to rediscover. It does not own the look.

Before writing, resolve the brand in this order and stop at the first hit:

1. A project-local skill for decks (often `make-presentation`) or a brand skill
   (often `brand-guidelines`). **If one exists, it wins on every conflict** with
   this skill: palette, type, logo placement, voice, output location, and any
   house rules. Apply its brand and keep the craft rules below.
2. A brand token file in the repository, commonly `brand/brand.json`,
   `brand/brand-manual.md`, or a stylesheet for the public site.
3. No brand source. Ask which of the dials below apply, or use the neutral
   defaults in [`template.html`](template.html) and say plainly that the result
   is unbranded.

### The brand contract

| Dial | What it sets |
| --- | --- |
| Canvas | Dark cinematic or light editorial, and the base colour behind everything. |
| Primaries | Two accent colours. These drive glows, gradient text, and kickers. |
| Ink | Heading and body colour on that canvas, plus a muted secondary. |
| Type | One sans for headings and body, one mono for kickers, pills, and labels. |
| Mark | The logo art and, importantly, where it may appear. |
| Footer | The standing footer string. |
| Voice | Headline case, tone, and any banned words or characters. |

In [`template.html`](template.html) these are CSS custom properties in a single
`:root` block. Overriding a brand is editing that block.

**Logo placement is a brand decision, not a default.** Houses differ sharply.
Common patterns: a mark on the title slide and nowhere else; no mark on the title
with a small fixed corner mark on content slides and the logo as hero on the
closing; or a mark only in the footer. Ask rather than assume, and apply one rule
consistently across the deck.

## Before writing

1. Resolve the brand as above.
2. Choose the canvas and commit to it. Dark cinematic suits pitches and launches.
   Light editorial suits board and internal decks, and survives printing better.
3. Choose length from the story, not a fixed slide count.
4. Facts from the project's knowledge base only. Use a visible placeholder when a
   figure is unknown, and list the placeholders on delivery.

## Quality bar

1. **Canvas with depth.** Dark: a near-black base in the brand's hue family, two
   soft radial glows in the primaries, and a faint masked grid. Light: a
   near-white sheet, dark ink, one accent. Commit to one, do not blend.
2. **Small palette with intent.** Two primaries carry the deck. Kickers may vary
   within that palette. Do not invent a rainbow.
3. **Gradient text sparingly.** Titles, section headlines, and stat numbers may
   use clip-text between the primaries. Never body copy.
4. **Left-aligned and editorial.** Uppercase kicker, then a strong headline, then
   structured support. One idea per slide.
5. **Components over bullet walls.** Cards, stats, pills, notes, short snippets.
   Cards only when they hold genuinely peer content. Otherwise use a note or a
   short list.
6. **Balance visual weight.** Boxes in a row should carry similar content and end
   at similar heights. Rebalance rather than ship a lopsided slide.
7. **Scale and space.** Large type and real whitespace. Density comes from
   structure, not from shrinking the font.

## Slide writing

Kicker, then headline, then support. Numbers become stats. Capabilities become
pills. Card copy stays short. Open with a title slide and close with a closing
slide.

### Balancing rules

- Peer ideas of similar length become equal cards. Very different volumes stack
  full width instead. Do not force empty boxes to make a grid.
- Stats in a row must share one shape, meaning short tokens of similar length.
- A tall column beside a short one: trim the tall one, add a peer element to the
  short one, or drop the two-column layout.
- At most one loose unboxed text block per slide, used as a caption above or
  below the structured content.

## Components in the template

Backdrop with glows and grid. Title slide. Kickers. Cards in two, three, and four
column variants. Stats. Pills. Notes. Two-column layout. Code snippet. Section
divider. Closing slide. Fixed footer, slide numbers, and progress bar.

## Build and share

1. Copy [`template.html`](template.html), set the token block, replace every
   `{{PLACEHOLDER}}`, and save to the project's output location.
2. Open in a browser. Arrow keys navigate, `Esc` opens the overview, `S` opens
   speaker notes.
3. Share the HTML file or host it. For PDF, append `?print-pdf` to the URL, then
   Print and Save as PDF.

## Layout gotchas

These are the expensive ones. Check them every time.

- **Reveal.js sets no base font family.** Without an explicit `font-family` on
  `.reveal` *and* on the heading elements, everything silently renders in Times.
  This is the single most common way a branded deck ships wrong.
- **Gradient clip-text needs room.** `background-clip: text` with a transparent
  fill clips descenders unless the line-height or padding is increased.
- **Gradient clip-text needs `width: fit-content`.** On a full-width block the
  text only shows the leftmost slice of the gradient, so a two-colour gradient
  renders as a single flat colour and never reaches the second.
- **Slide numbers render as links.** Style `.slide-number a` or the number shows
  as a blue underlined link over the design.
- **Backgrounds vanish in print-PDF.** Dark canvases need
  `print-color-adjust: exact` to survive the export.
- **Relative asset paths break on move.** A deck saved to an output directory
  loses logo and image paths. Inline SVG and embed raster images as data URIs so
  the file travels alone.
- **Content overflows silently.** Reveal scales slides to the viewport, so an
  overfull slide shrinks rather than warning. Review at presentation size.

## Output contract

Deliver the HTML path, explicitly marked a draft. List every remaining
placeholder and every fact that lacks a source. Never fabricate statistics.
Presenting or sending the deck outward is the operator's decision, not the
agent's.

## Quality checklist

- [ ] A real canvas, dark with backdrop or deliberately light editorial, not flat
      default reveal.
- [ ] Two primaries lead, kickers restrained, no accent soup.
- [ ] One idea per slide, balanced weight, short copy.
- [ ] Fonts correct and verifiably not Times, descenders intact.
- [ ] Gradient text reaches both colours.
- [ ] Slide number neutral rather than a blue link.
- [ ] Title and closing slides present, logo rule applied consistently.
- [ ] No `.pptx` unless it was explicitly asked for after the HTML.
