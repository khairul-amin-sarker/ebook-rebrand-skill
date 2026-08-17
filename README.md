# PDF-Native Ebook Rebrand Skill

A reusable agent skill for recreating and rebranding a licensed/authorized ebook PDF while preserving the source publication's page geometry, typography, spacing, alignment, page count, colors, and infographics.

The workflow is designed for Claude Code, Codex, ChatGPT, or other coding/agent environments that can inspect PDFs and generate files.

## What this skill does

- Treats the source PDF as the visual specification.
- Preserves exact page size/aspect ratio and fixed-layout geometry.
- Preserves source fonts, text scale, spacing, headers, footers, and alignment where legally/technically possible.
- Recreates or preserves infographics as SVG/native PDF vectors instead of AI-generated raster approximations.
- Replaces old branding comprehensively: logo, watermark, title, copyright, website, publisher/author labels, metadata, and hidden legacy strings.
- Uses a 3-page calibration stage before full-book production.
- Performs structural, typography, branding, vector, visual-match, and mobile-readability QA.

## Files

- `SKILL.md` — the complete agent workflow and operating rules.
- `REQUIREMENTS_TEMPLATE.md` — fill this in for each new ebook project.
- `QA_CHECKLIST.md` — final pre-delivery quality checks.
- `EXAMPLE_BOI_VERSE_REQUIREMENTS.md` — example requirement block from a real Boi Verse rebrand workflow.

## How to use with Claude / Claude Code

Give Claude this repository URL and instruct it to:

1. Read `SKILL.md` fully.
2. Treat `SKILL.md` as the execution SOP for the task.
3. Ask for/upload the brand logo and source ebook PDF if they are not already provided.
4. Parse the user's project instructions using `REQUIREMENTS_TEMPLATE.md`.
5. Follow the calibration gate before full production unless the user explicitly skips it.
6. Run `QA_CHECKLIST.md` before claiming completion.

Example instruction:

```text
Use this repository as the skill/SOP for the ebook task:
https://github.com/khairul-amin-sarker/ebook-rebrand-skill

Read SKILL.md completely, then follow it strictly.
I will provide my logo, source PDF, and requirements in the chat.
```

## Rights requirement

This skill is intended only for source ebooks the user has permission, license, or authorization to edit/rebrand/reuse.

## Core output target

A PDF-native fixed-layout edition with selectable text where possible, embedded fonts, vector/SVG infographics, fixed coordinate placement, and no unwanted trace of the legacy brand.
