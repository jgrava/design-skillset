---
description: Evaluate UI screenshots and synthesize a production-ready theme document for the theme library.
argument-hint: "[screenshots or path to screenshots to evaluate]"
---
# /build-theme
Evaluate screenshots and build a theme document.
## Steps
1. **Evaluate** — Analyze each screenshot across 10 dimensions using `theme-builder` skill.
2. **Name** — Identify the dominant visual language, propose a 2-3 word theme name.
3. **Organize** — Create theme directory in `~/Workspaces/Design-System/theme-library/{theme-name}/`.
4. **Approve** — Present theme name and reasoning to the user for approval.
5. **Typography** — Specify font sources (Adobe Typekit, Google Fonts, self-hosted, or system) and exact weights using `theme-builder` skill.
6. **Synthesize** — Produce the full theme document from the reference template using `theme-builder` skill.
## Output
A named theme directory containing individual evaluation files, font specification, and a production-ready theme document usable as a direct prompt for building UIs.
