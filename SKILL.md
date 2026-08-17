---
name: pdf-native-ebook-rebrand-recreator
description: Rebrand and recreate a licensed source ebook as a PDF-native fixed-layout edition while preserving page size, page count, typography, spacing, alignment, colors, and infographics, and replacing all legacy branding with the user's brand.
version: 1.0.0
---

# PDF-Native Ebook Rebrand & Recreation Skill

## Purpose

Use this skill when the user provides a licensed/authorized source ebook PDF and wants a new branded edition that stays visually as close as possible to the source while replacing the source brand, title, copyright, watermark, logo, website, author/publisher labels, background color, and any other explicitly requested elements.

The target output is **not** a screenshot-based or image-generated imitation. The target is a **PDF-native, fixed-layout recreation** with selectable text where possible, embedded fonts, vector/SVG infographics, fixed page coordinates, and consistent brand replacement across the entire document.

## Core Principle

Treat the source PDF as the **visual specification**.

Do not redesign unless the user asks for redesign. Do not improve, modernize, simplify, recolor, or reinterpret the layout by default. Preserve the source's visual system and only apply requested brand/content changes.

## Rights Gate

Before full production, confirm that the user states they have the right, license, or permission to edit/rebrand/reuse the source PDF and its content/graphics.

If the user has not stated this, ask once. If they have already stated it in the conversation, do not ask again.

## Input Contract

The agent should be able to work from these inputs:

1. **Brand logo** — preferably SVG, PDF vector logo, or transparent PNG.
2. **Source ebook PDF** — the licensed/authorized source.
3. **Requirements text** — the user's requested replacements and constraints.

The upload order does not matter. Do not start the full build until all essential inputs are available.

### Parse Requirements Into This Internal Schema

```yaml
brand_name: ""
brand_name_exact_case: ""
logo_file: ""
source_pdf: ""
new_ebook_title: ""
old_ebook_title_terms: []
copyright_year: ""
copyright_line: ""
written_by_line: ""
publisher_line: ""
website: ""
legacy_brand_terms_to_remove: []
watermark:
  use_logo: true
  use_brand_text: true
  text: ""
  rotation: "match-source"
  opacity: "match-source"
  scale: "match-source"
background_color: "match-source"
preserve_source_content: true
preserve_page_count: true
preserve_page_size: true
preserve_typography: true
preserve_spacing: true
preserve_alignment: true
preserve_infographic_colors: true
preserve_infographic_geometry: true
infographic_output: "svg/vector"
calibration_required: true
calibration_page_count: 3
output_filename: ""
notes: ""
```

If a requirement is unclear but can be safely inferred from the source or earlier conversation, infer it. Ask only when the missing value can materially change the final output.

---

# Production Workflow

## Phase 1 — Source Audit

Inspect the entire source PDF before editing.

Create a source audit containing:

- Total page count.
- Exact MediaBox/CropBox page dimensions and aspect ratio.
- Whether every page uses the same size.
- Embedded font families and styles.
- Dominant text sizes.
- Heading sizes.
- Line height / leading patterns.
- Paragraph spacing.
- Left/right/top/bottom margins.
- Header and footer coordinates.
- Page-number position and style.
- Copyright/publisher placement.
- Watermark size, opacity, rotation, position, and frequency.
- Background color(s).
- Brand palette from actual vector fill/stroke values where possible.
- Recurring page families/templates.
- All pages containing infographics, charts, icons, diagrams, illustrations, tables, or decorative vector elements.
- Which graphics are vector, raster, or mixed.
- All legacy brand strings, domains, logos, watermarks, and metadata that must be removed.

### Do Not Trust OCR or Parsed Text Alone

For complex PDFs, parsed text can contain broken Bengali glyphs or corrupted character order. Use the rendered page visual and the PDF text/vector layer together.

Prefer these sources in order:

1. Original PDF text/vector objects.
2. Rendered page visual inspection.
3. OCR only as a last resort.

## Phase 2 — Build a Design Specification

Create a reusable design spec from the source.

At minimum, lock:

- Page width/height.
- Content box coordinates.
- Header baseline.
- Header divider position and thickness.
- Page number coordinate.
- Copyright coordinate.
- Body text font family/style/size.
- Heading font family/style/size.
- Line spacing.
- Paragraph gap.
- Watermark bounding box.
- Background fill.
- Accent palette.
- Standard footer locations.

Use the source PDF's actual measurements when possible instead of estimating from screenshots.

## Phase 3 — Identify Page Families

Group pages into reusable fixed-layout families, for example:

1. Cover.
2. Quote / opening page.
3. Copyright / disclaimer.
4. Table of contents.
5. Standard text-heavy page.
6. Section-opening page.
7. Text + infographic page.
8. Full infographic page.
9. Case-study page.
10. Back cover.

Do not rebuild every page as an unrelated design if multiple pages share the same system.

## Phase 4 — Calibration Gate

Before processing the whole book, create **3 representative calibration pages** unless the user explicitly tells you to skip calibration.

Choose:

- One text-heavy page.
- One heading + infographic page.
- One complex infographic or special-layout page.

The calibration output must already include the user's requested branding, background, watermark, title/copyright updates, and vector recreation policy.

Ask the user to approve or request changes.

Once approved, freeze the design system. Do not drift from the approved calibration during full production.

## Phase 5 — PDF-Native Recreation

### Page Canvas

Use a fixed-coordinate canvas matching the source MediaBox exactly.

Do not silently convert the source to A4, Letter, or another standard page size.

### Text

Preserve the original font family and metrics when legally and technically possible.

Preferred behavior:

- Reuse the original PDF text objects when content is unchanged.
- Preserve embedded font usage where allowed.
- If the exact font is unavailable, ask the user for the licensed font file or use the closest permitted substitute only with user approval.
- Never replace the full page with a raster image just to preserve appearance.

For Bengali text, verify shaping, ligatures, vowel signs, conjuncts, punctuation, and line breaks visually after rendering.

### Page Count and Content Fit

If the user wants the same page count:

1. Preserve font size first.
2. Preserve line spacing and margins second.
3. Preserve page count third.
4. Do not aggressively shrink text to force fit.

If replacement content is longer than the original text box can hold, first attempt small non-destructive adjustments within the source's natural tolerance. If it still does not fit, flag the specific page and request copy shortening or explicit permission to modify typography.

If content is unchanged, preserve the original line wrapping wherever possible.

---

# Infographic & Vector Policy

## Mandatory Default

Infographics, diagrams, icons, charts, and decorative shapes should be delivered as **SVG/vector or native PDF vector objects**, not AI-generated raster images.

## Preferred Method Order

1. Extract and reuse the source PDF's original vector paths when permitted.
2. Reconstruct the graphic from measured PDF geometry.
3. Trace/recreate as SVG using exact source coordinates and colors.
4. Use raster only if the source itself is raster and vector recreation is impractical.

## Color Matching

Do not estimate infographic colors by eye if actual fill/stroke values can be extracted from the PDF.

Lock source colors as exact RGB/HEX/CMYK equivalents and reuse them consistently.

Do not recolor unless the user explicitly asks.

## Geometry Matching

Preserve:

- Node positions.
- Connector paths.
- Circle/rectangle sizes.
- Corner radii.
- Stroke widths.
- Icon placement.
- Text alignment.
- Label sizing.
- Internal padding.
- Group scale.
- Bounding-box position on the page.

Image generation tools are **not** the default method for business infographics that need same-to-same geometry and readable text.

---

# Branding Replacement Policy

Replace the source brand comprehensively.

Search for and remove/replace:

- Logos.
- Wordmarks.
- Watermarks.
- Copyright lines.
- Header labels.
- Footer labels.
- Website/domain names.
- Email addresses if brand-owned.
- "Written by" / author / publisher labels.
- Cover branding.
- Back-cover branding.
- PDF metadata fields such as Title, Author, Subject, Keywords, Creator, Producer where appropriate.
- Hidden text objects containing the legacy brand.

## Exact Brand Casing

If the user provides brand casing, preserve it exactly.

Example:

`Boi Verse`

means capital `B`, lowercase `oi`, space, capital `V`, lowercase `erse`.

Do not silently normalize it to `Boiverse`, `BOI VERSE`, or any other variant.

## Watermark Construction

If the user requests logo + brand text in the watermark:

- Use the logo and the exact brand text as a grouped watermark.
- Match the source watermark's approximate visual weight, rotation, position, and opacity.
- Keep it subtle enough not to reduce readability.
- Prefer vector/transparency rather than flattened raster watermarking.

---

# Background Policy

If the user requests a new background color:

- Apply it as a true page background fill, not as a screenshot overlay.
- Preserve all original foreground colors unless the user requests otherwise.
- Verify text and infographic contrast on mobile-size rendering.

If the user says "between white and off-white," choose a very subtle warm-neutral off-white and keep it consistent across body pages unless the source has intentional colored pages.

---

# Full-Book Processing

After calibration approval:

1. Apply the locked master geometry to every page.
2. Perform branding replacement page-by-page.
3. Recreate or preserve every infographic according to the vector policy.
4. Preserve page order and page count if required.
5. Update title/copyright/publisher/branding consistently.
6. Preserve source content unless the user asked for edits.
7. Render the full PDF for visual QA.

Do not claim the full book is complete until the final PDF exists and passes QA.

---

# QA Checklist

## Structural QA

- [ ] Page count matches the requested count.
- [ ] Every page has the correct MediaBox/CropBox.
- [ ] Page order matches the source.
- [ ] No blank or duplicate pages were introduced.

## Typography QA

- [ ] Bengali text renders correctly.
- [ ] No missing glyph boxes.
- [ ] No broken conjuncts.
- [ ] No unexpected line-wrap drift on unchanged content.
- [ ] Font sizes match the approved calibration.
- [ ] Header/footer text uses the approved font and scale.

## Branding QA

Run text and object searches for all legacy brand terms.

- [ ] Legacy brand name absent.
- [ ] Legacy domain absent.
- [ ] Legacy copyright absent.
- [ ] Legacy watermark absent.
- [ ] Legacy logo absent.
- [ ] New brand spelling/casing is exact everywhere.
- [ ] Copyright year is correct everywhere.
- [ ] Cover and back cover use the new brand.
- [ ] Metadata has been updated.

## Infographic QA

- [ ] Infographics are vector/native PDF where required.
- [ ] Source palette is preserved exactly.
- [ ] Labels are readable.
- [ ] Geometry matches the source.
- [ ] No unwanted rasterization of entire pages.

## Visual QA

Render source and recreated pages at approximately 150–200 DPI or higher.

For representative pages, compare side-by-side and/or with a difference overlay.

Check:

- Header baseline.
- Divider position.
- Text box edges.
- Paragraph spacing.
- Heading position.
- Infographic bounding box.
- Watermark scale/rotation/opacity.
- Footer/logo placement.

Correct systematic drift before final delivery.

## Mobile QA

Inspect the final PDF at common phone-width viewing conditions.

Verify:

- Body text is comfortably readable when the page is fit to screen.
- Infographic labels remain legible.
- No text is clipped.
- Off-white background does not reduce contrast.
- Watermark does not interfere with body text.

---

# Failure Modes to Avoid

Never do these unless the user specifically requests them:

- Rebuild the whole book as one image per page.
- Use image generation for exact infographic recreation.
- Change the original color palette "for branding" when the user said keep colors.
- Convert the page to a different aspect ratio.
- Shrink body text significantly to make content fit.
- Guess the font when the source font can be identified.
- Leave hidden legacy brand strings inside the PDF.
- Claim "same-to-same" without visual QA.
- Start all pages before testing representative calibration pages, unless the user explicitly skips calibration.

---

# Agent Response Behavior

When beginning the task, briefly summarize the parsed requirements and state what is locked.

During production, do not repeatedly ask for information already provided.

If a source inconsistency is discovered, report the exact page(s) and the smallest decision needed from the user.

When finished, deliver:

1. Final PDF.
2. Optional calibration PDF if used.
3. Short QA summary stating page count, page size, fonts, vector infographic status, brand-removal check, and major replacements.

Do not claim a file was created unless it actually exists.

---

# Example Requirement Block

```text
Source PDF: attached
Brand logo: attached
Brand name: Boi Verse
Brand casing must be exactly: Boi Verse
New ebook title: Customer এর মন জয় করার কৌশল
Copyright year: 2026
Header right: © 2026 Boi Verse e-books
Written by: Boi Verse
Watermark: logo + text “Boi Verse”, same angle/opacity/position as source
Background: very subtle off-white between pure white and cream
Remove all traces of: E GRAHOK, egrahok.com, old copyright, old logo, old watermark
Keep: same page count, page size, fonts, spacing, page alignment, infographic colors and geometry
Infographics: recreate/preserve as SVG/vector, not AI-generated raster
Final output: PDF-native PDF
Calibration: 3 pages before full build
```

---

# Completion Standard

The task is complete only when the new ebook feels like the same publication system as the licensed source, but all requested identity-level elements belong to the user's brand and no visible or hidden trace of the legacy brand remains.
