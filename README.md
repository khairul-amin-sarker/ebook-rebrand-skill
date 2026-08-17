# PDF-Native Ebook Rebrand Skill

A reusable agent skill/plugin for recreating and rebranding a licensed/authorized ebook PDF while preserving the source publication's page geometry, typography, spacing, alignment, page count, colors, and infographics.

The workflow is designed for **Claude Code**, Codex, ChatGPT, and other coding/agent environments that can inspect PDFs and generate files.

## What this skill does

- Treats the source PDF as the visual specification.
- Preserves exact page size/aspect ratio and fixed-layout geometry.
- Preserves source fonts, text scale, spacing, headers, footers, and alignment where legally/technically possible.
- Recreates or preserves infographics as SVG/native PDF vectors instead of AI-generated raster approximations.
- Replaces old branding comprehensively: logo, watermark, title, copyright, website, publisher/author labels, metadata, and hidden legacy strings.
- Uses a 3-page calibration stage before full-book production.
- Performs structural, typography, branding, vector, visual-match, and mobile-readability QA.

# Claude Code: persistent install + slash command

This repository now includes a real Claude Code plugin and marketplace manifest.

### Install once

Inside Claude Code, run:

```text
/plugin marketplace add khairul-amin-sarker/ebook-rebrand-skill
/plugin install ebook-rebrand@ebook-rebrand-skill
```

After installation, the plugin is stored by Claude Code on that machine and can be used in later Claude Code sessions without downloading `SKILL.md` again.

### Use anytime

```text
/ebook-rebrand
```

Or pass a short instruction:

```text
/ebook-rebrand Use the attached source PDF and logo. Keep the original page count, typography, spacing, infographic colors and geometry. Replace all old branding with my new brand.
```

The command loads the full PDF-native ebook-rebrand skill automatically.

> Note: persistent plugin installation applies to Claude Code environments where you control the local Claude Code installation. A temporary hosted Claude chat/container may reset its filesystem and cannot guarantee permanent installation across chats.

## Give Claude only this GitHub link

You can tell Claude Code:

```text
Install the Claude Code ebook-rebrand plugin from this repository and make it available as a slash command:
https://github.com/khairul-amin-sarker/ebook-rebrand-skill

Use the repository's .claude-plugin marketplace configuration. After installation I want to invoke it with /ebook-rebrand.
```

If Claude Code needs the explicit commands, they are:

```text
/plugin marketplace add khairul-amin-sarker/ebook-rebrand-skill
/plugin install ebook-rebrand@ebook-rebrand-skill
```

## Project-level fallback

If the repository is simply cloned and Claude Code is started from inside it, the repo also contains:

```text
.claude/commands/ebook-rebrand.md
```

so `/ebook-rebrand` can be used as a project-level command even without plugin installation.

## Cross-agent files

- `SKILL.md` — authoritative ebook-rebrand SOP.
- `CLAUDE.md` — Claude Code project instructions; imports the SOP/support files.
- `AGENTS.md` — portable instructions for Codex and other agents.
- `.claude/commands/ebook-rebrand.md` — project-level `/ebook-rebrand` command.
- `.claude-plugin/marketplace.json` — Claude Code marketplace manifest.
- `plugins/ebook-rebrand/` — installable Claude Code plugin.
- `REQUIREMENTS_TEMPLATE.md` — project intake template.
- `QA_CHECKLIST.md` — final pre-delivery quality checks.
- `EXAMPLE_BOI_VERSE_REQUIREMENTS.md` — example requirement block from a Boi Verse rebrand workflow.

## Normal ebook workflow

After invoking `/ebook-rebrand`, provide:

1. The authorized/licensed source ebook PDF.
2. Your brand logo.
3. Your requirements: new title, exact brand casing, copyright year/line, watermark instructions, background changes, old brand strings to remove, etc.

The workflow is:

**source audit → design specification → 3-page calibration → approval → full PDF-native rebuild → vector infographic pass → full QA → final PDF**

## Rights requirement

This skill is intended only for source ebooks the user has permission, license, or authorization to edit/rebrand/reuse.

## Core output target

A PDF-native fixed-layout edition with selectable text where possible, embedded fonts, vector/SVG infographics, fixed coordinate placement, and no unwanted trace of the legacy brand.
