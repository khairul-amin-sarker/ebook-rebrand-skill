# Agent Instructions

This repository is a portable SOP for recreating and rebranding authorized ebook PDFs while preserving the source publication's visual system.

## Start here

Read these files before execution:

- `SKILL.md` — authoritative workflow.
- `REQUIREMENTS_TEMPLATE.md` — requirement schema.
- `QA_CHECKLIST.md` — completion gate.

## Agent rules

- Treat the source PDF as the visual specification.
- Preserve page size/aspect ratio, typography, spacing, alignment, page count, and infographic geometry/colors unless the user requests changes.
- Use PDF-native fixed-coordinate construction.
- Preserve/selectively reuse PDF text objects when appropriate.
- Prefer extracted/reconstructed SVG/native PDF vectors for infographics.
- Do not use AI image generation as the default way to recreate exact business infographics.
- Do not rasterize whole pages merely to preserve visual appearance.
- Search for legacy branding in visible text, hidden text, metadata, logos, domains, watermarks, headers, footers, cover, and back cover.
- Respect exact brand casing supplied by the user.
- Use a 3-page calibration gate before full-book production unless explicitly skipped.
- Render and visually QA before completion.
- Never claim an output exists before verifying the file exists.

## Cross-agent compatibility

For Claude Code, use `CLAUDE.md` and `/ebook-rebrand`.
For Codex or other agents, use this `AGENTS.md` plus `SKILL.md` as the operating instructions.
