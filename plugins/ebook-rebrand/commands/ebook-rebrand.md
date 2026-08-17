---
name: ebook-rebrand
description: Rebrand an authorized ebook PDF using the PDF-native fixed-layout workflow
argument-hint: [optional requirements or task note]
---

Load and follow the plugin skill at:

@${CLAUDE_PLUGIN_ROOT}/skills/ebook-rebrand/SKILL.md

Also use these support files when useful:

@${CLAUDE_PLUGIN_ROOT}/templates/REQUIREMENTS_TEMPLATE.md
@${CLAUDE_PLUGIN_ROOT}/templates/QA_CHECKLIST.md

User arguments for this run:

$ARGUMENTS

Execute the workflow from the skill. Identify the source PDF, logo, and requirements from the current workspace/conversation; ask only for missing essentials. Do not begin full production before the source audit and calibration gate unless the user explicitly skips calibration. Do not claim completion until the final PDF exists and QA has passed.
