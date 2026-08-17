# Claude Code Instructions

This repository packages the **PDF-Native Ebook Rebrand & Recreation** workflow.

## Required behavior

Before doing any ebook rebrand/recreation work, read and follow:

@SKILL.md
@REQUIREMENTS_TEMPLATE.md
@QA_CHECKLIST.md

Treat `SKILL.md` as the authoritative SOP.

## Core execution rule

When the user invokes `/ebook-rebrand` or asks to use this repository for an ebook rebrand task:

1. Confirm the source ebook is authorized/licensed for modification if the user has not already said so.
2. Collect or identify the source PDF, the user's brand logo, and the requirements.
3. Parse requirements using `REQUIREMENTS_TEMPLATE.md`.
4. Audit the complete PDF before rebuilding it.
5. Preserve source page geometry, font metrics, spacing, alignment, page count, and infographic colors/geometry unless the user explicitly requests changes.
6. Use PDF-native fixed-layout construction.
7. Prefer SVG/native PDF vectors for infographics instead of AI-generated raster images.
8. Produce 3 representative calibration pages before full production unless the user explicitly skips calibration.
9. After approval, freeze the design system and complete the full book.
10. Run `QA_CHECKLIST.md` before claiming completion.

Do not claim files were created unless they actually exist.

## Portable usage

This repository also contains a Claude Code plugin package under `plugins/ebook-rebrand/` and a project-level slash command under `.claude/commands/ebook-rebrand.md`.
