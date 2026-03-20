# Theme Builder

Build production-ready UI themes from design screenshots with precise typography sourcing.

## Overview

This plug-in provides a structured process for analyzing visual designs across 10 dimensions — color, typography, spacing, borders, depth, texture, components, iconography, motion, and mood — then synthesizing those observations into reusable theme documents that serve as direct prompts for building UIs.

## Skills

| Skill | Description |
|-------|-------------|
| **theme-builder** | Evaluate screenshots, specify typography, name themes, and synthesize production-ready theme documents |

## Commands

| Command | Description |
|---------|-------------|
| `/build-theme` | Run the full theme building pipeline on a set of screenshots |

## Process

1. **Evaluate** — Each screenshot gets a detailed `.md` evaluation covering 10 design dimensions
2. **Name & Organize** — Common visual language is identified and a 2-3 word theme name proposed
3. **Typography** — Lock down exact fonts and loading method (Adobe Typekit, Google Fonts, self-hosted, or system fonts)
4. **Synthesize** — Evaluations and font specs are distilled into a single theme document following a proven template

## Font Sources

The theme builder supports four font sourcing strategies:

| Source | Best For | Requires |
|--------|----------|----------|
| **Adobe Typekit** | Premium typefaces, Creative Cloud teams | Active CC subscription + kit ID |
| **Google Fonts** | Free, widely available fonts | Nothing — free and open |
| **Self-Hosted** | Maximum control, custom/licensed fonts | Font files (woff2/woff) |
| **System Fonts** | Zero load time, maximum performance | Nothing — uses OS fonts |

## Theme Library

Themes are saved to `~/Workspaces/Design-System/theme-library/`:

```
theme-library/
├── minimalist-monochrome/
│   ├── evaluations/
│   │   ├── evaluation-hero-section.md
│   │   ├── font-specification.md
│   │   └── ...
│   └── minimalist-monochrome.md
└── ...
```

## References

- `skills/theme-builder/references/theme-template.md` — The output template used for synthesizing theme documents
