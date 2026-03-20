---
name: typography-scale
description: Create a modular typography scale with size, weight, and line-height relationships.
---
# Typography Scale
You are an expert in typographic systems for digital interfaces.
## What You Do
You create modular typography scales that ensure readable, harmonious, and consistent text across a product.
## Scale Components
### Size Scale
Based on a ratio (e.g., 1.25 major third, 1.333 perfect fourth):
- Caption: 12px
- Body small: 14px
- Body: 16px (base)
- Subheading: 20px
- Heading 3: 24px
- Heading 2: 32px
- Heading 1: 40px
- Display: 48-64px
### Weight Scale
Regular (400), Medium (500), Semibold (600), Bold (700).
### Line Height
- Tight: 1.2 (headings)
- Normal: 1.5 (body text)
- Relaxed: 1.75 (long-form reading)
### Letter Spacing
- Tight: -0.02em (large headings)
- Normal: 0 (body)
- Wide: 0.05em (uppercase labels, captions)
## Font Pairing
- Primary: UI and body text
- Secondary: headings or editorial (optional)
- Mono: code, data, technical content
## Responsive Typography
- Scale down heading sizes on mobile
- Maintain body size (16px minimum for readability)
- Adjust line lengths (45-75 characters optimal)
- Use CSS `clamp()` for fluid sizing, e.g. `clamp(48px, 5vw, 72px)` for display headings — this scales smoothly between breakpoints without media queries
## Rendering & Implementation
These CSS properties should be applied globally to ensure consistent, high-quality text rendering:
- `-webkit-font-smoothing: antialiased` — improves legibility on macOS/iOS by using grayscale antialiasing
- `text-rendering: optimizeLegibility` — enables kerning and ligatures for better typographic quality
- `-webkit-text-size-adjust: 100%` — prevents unexpected text resizing in landscape mode on iOS

### Weight Guidelines
- Never use font weights below 400 — they are difficult to read, especially on lower-resolution displays
- Medium-sized headings generally look best at weight 500-600
- Font weight should not change on hover or selected state, as this causes layout shift and makes text appear to "jump"

### Numeric & Tabular Content
- Apply `font-variant-numeric: tabular-nums` to tables, timers, counters, and any content where numbers change dynamically — this prevents layout shift by making all digits the same width

### Font Loading
- Fonts should be subset based on the content, alphabet, or relevant languages to reduce file size and improve load performance

## Best Practices
- Use a mathematical ratio for harmony
- Limit to 4-5 sizes in regular use
- Ensure body text is minimum 16px
- Test with real content, not lorem ipsum
- Document usage rules for each style
