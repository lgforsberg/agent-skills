---
name: html-document
description: Produce print-ready, editorial-quality long-form documents as a single self-contained HTML file that exports cleanly to PDF, covering proposals, quotes, statements of work, letters, reports, memos, briefs, and whitepapers. Defaults to HTML and PDF rather than Word. Use when a polished document is wanted for review, print, or sending. Defers to any project-local brand skill for palette, type, and logo.
---

# HTML document (print-first, exports to PDF)

Produce a **draft** long-form document as one self-contained HTML file styled for
print. The invariant is craft: it must look deliberately typeset, never like
markdown dumped to PDF.

For on-screen slides, use the `html-presentation` skill instead. For a rough
internal note, plain markdown is fine. This skill is for finished work.

**Do not produce `.docx` by default.** If a counterpart insists on Office,
convert from the PDF or ask. Do not build a Word pipeline unprompted.

## Brand comes from the project, craft comes from here

This skill owns the craft layer: structure, typography, print behaviour, and the
bugs that cost hours to rediscover. It does not own the look.

Before writing, resolve the brand in this order and stop at the first hit:

1. A project-local skill for documents (often `make-document`) or a brand skill
   (often `brand-guidelines`). **If one exists, it wins on every conflict** with
   this skill: palette, type, logo, voice, output location, and any house rules.
   Apply its brand and keep the craft rules below.
2. A brand token file in the repository, commonly `brand/brand.json`,
   `brand/brand-manual.md`, or a stylesheet for the public site.
3. No brand source. Ask which of the dials below apply, or use the neutral
   defaults in [`template.html`](template.html) and say plainly that the result
   is unbranded.

### The brand contract

A brand needs to supply only these dials. Everything else is craft.

| Dial | What it sets |
| --- | --- |
| Page | Paper size and margins. A4 outside North America, US Letter inside it. |
| Ink | Body colour and a muted secondary. Near-black in the brand's hue family, not `#000`. |
| Accent | One lead accent, an optional second, and a pale tint for table headers and callouts. |
| Type | One sans for body and titles, one mono for eyebrows, labels, and table chrome. |
| Mark | The logo art and where it may appear. |
| Footer | The standing footer string. |
| Voice | Headline case, tone, the legal name, and any banned words or characters. |

In [`template.html`](template.html) the first six are CSS custom properties in a
single `:root` block. Overriding a brand is editing that block.

## Before writing

1. Resolve the brand as above.
2. Decide character from type, audience, and tone. A one-page quote and a board
   brief should not feel identical. Choose the sections actually needed rather
   than filling every section the template offers.
3. Pull facts from the project's knowledge base. Never invent figures, dates,
   prices, org numbers, or legal names. Use a visible placeholder when a value is
   unknown, and list the placeholders on delivery.

## Quality bar

1. **Print-first, screen-second.** Design for `@page`. Deliberate breaks,
   orphan and widow control, `break-inside: avoid` on tables, callouts, and
   figures. On screen, floating sheets with a soft shadow are fine.
2. **Clear type roles.** Distinguish roles through weight, size, case, and
   tracking rather than by adding faces. Two families is usually the ceiling.
3. **One restrained accent.** The lead accent carries the document. A second
   accent appears at most once, as a single emphasis. Neither is body colour.
4. **Typographic craft.** Uppercase labels with letter-spacing, tabular figures
   for money, right-aligned currency columns, a short measure for leads, and a
   generous line-height around 1.55.
5. **Whitespace and restraint.** Wide margins, air between sections, no clip-art,
   no gradient washes, no decorative cards that hold nothing.

## Components in the template

Cover with eyebrow, title, subtitle, accent rule, metadata grid, and
confidentiality line. Section headings with a mono label and rule. Body with
`.lead` and `.subhead`. Accent bullets. `.info-table` and `.cost-table`.
`.callout`. Metric cards. Figures with captions. A repeating print footer.

Structure with `<section class="sheet">` per printed page, or let content flow
and place `<div class="page-break">` where a page must start.

Use only what the document needs. Deleting unused components is part of the job.

## Build and export

1. Copy [`template.html`](template.html), set the token block, replace every
   `{{PLACEHOLDER}}`, and save to the project's output location.
2. Preview in a browser.
3. Export PDF with Print then Save as PDF, or headless Chrome:

```bash
chrome --headless --disable-gpu \
  --print-to-pdf="out.pdf" --no-pdf-header-footer \
  "file:///absolute/path/to/document.html"
```

On macOS the binary is usually
`/Applications/Google Chrome.app/Contents/MacOS/Google Chrome`.

4. Open the PDF and count its pages against the sheet count before delivering.
5. Keep local images beside the HTML if the folder is sent as-is. Better still,
   inline SVG and embed raster images as data URIs so the file travels alone.

## Layout gotchas

These are the expensive ones. Check them every time.

- **Backgrounds vanish in PDF.** Chrome drops background colours and images when
  printing unless `print-color-adjust: exact` is set. Any dark cover or tinted
  table header needs it, or the cover prints white with white text on it.
- **Screen sheets and printed pages diverge.** They only match if each sheet
  starts a page in print CSS and each sheet's content actually fits. A sheet that
  overflows silently becomes two pages. Count pages in the exported PDF.
- **Flex-anchored covers collapse in print.** A cover relying on
  `justify-content: space-between` needs an explicit print `min-height`, or the
  metadata floats up under the title.
- **Fallback stacks lie.** Verify a face actually loaded with
  `document.fonts.check('12px "Family Name"')` rather than trusting the CSS
  declaration. A missing webfont silently renders the fallback.
- **Headless hosts lack local fonts.** A face installed on the author's machine
  may be absent wherever the PDF is generated. Prefer a system stack or an
  embedded webfont, and treat the fallback as a real design state.
- **Scanning a PDF for font names needs stream inflation.** Compressed streams
  make a naive text search report false negatives.
- **Tables split badly by default.** `break-inside: avoid` on rows, plus
  `display: table-header-group` on `thead` so headers repeat across pages.

## Output contract

Deliver the HTML path, and the PDF path when exported, explicitly marked a draft.
List every remaining placeholder and every fact that lacks a source. Never invent
figures. Sending the document outward is the operator's decision, not the agent's.

## Quality checklist

- [ ] Type roles distinct, ink is not pure black, accent used with restraint.
- [ ] Cover complete, labels letter-spaced, money tabular and right-aligned.
- [ ] Page breaks deliberate, tables and callouts do not split awkwardly.
- [ ] Backgrounds survive the PDF export.
- [ ] Correct paper size, even margins, every placeholder resolved.
- [ ] PDF page count matches the intended sheet count.
- [ ] Reads as designed, not as exported markdown.
- [ ] No `.docx` unless it was explicitly asked for after the HTML and PDF.
