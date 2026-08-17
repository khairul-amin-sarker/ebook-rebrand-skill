---
description: Rebrand an authorized ebook PDF using the PDF-native fixed-layout SOP in this repository
argument-hint: [optional requirements or task note]
---

Use this repository's ebook rebrand workflow for the current task.

First read these files completely:

- @SKILL.md
- @REQUIREMENTS_TEMPLATE.md
- @QA_CHECKLIST.md

Treat `SKILL.md` as authoritative.

User arguments for this run:

$ARGUMENTS

Execution rules:

1. Identify the source PDF, brand logo, and user's requirements from the current conversation/workspace.
2. If rights/license/permission to modify the source has not already been stated, ask once before full production.
3. Parse the requirements into the schema in `SKILL.md`.
4. Audit the full PDF before modifying it.
5. Preserve exact page geometry, font metrics, spacing, alignment, page count, infographic colors, and infographic geometry unless the user explicitly requests a change.
6. Use PDF-native fixed-coordinate output. Do not flatten the whole book to page screenshots.
7. Use extracted/reconstructed SVG or native PDF vectors for infographics whenever practical.
8. Create 3 calibration pages (text-heavy, infographic, complex/special layout) before full production unless the user explicitly skips calibration.
9. After approval, freeze the design spec and process the full ebook.
10. Run the complete QA checklist, including legacy-brand search, before claiming completion.
11. Deliver the actual final PDF and a concise QA summary.

If required inputs are missing, ask only for the missing items instead of restarting the whole intake.
