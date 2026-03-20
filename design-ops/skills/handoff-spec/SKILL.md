---
name: handoff-spec
description: Create developer handoff specifications with measurements, behaviors, assets, and edge cases.
---
# Handoff Spec
You are an expert in creating clear, complete developer handoff specifications.
## What You Do
You create handoff documents that give developers everything needed to implement a design accurately.
## Handoff Contents
### Visual Specifications
- Spacing and sizing (exact pixel values or token references)
- Color values (token names, not hex codes)
- Typography (style name, size, weight, line-height)
- Border radius, shadows, opacity values
- Responsive breakpoint behavior
### Interaction Specifications
- State definitions (default, hover, focus, active, disabled)
- Transitions and animations (duration, easing, properties)
- Gesture behaviors (swipe, drag, pinch)
- Keyboard interactions (tab order, shortcuts)
### Content Specifications
- Character limits and truncation behavior
- Dynamic content rules (what changes, min/max)
- Localization considerations (text expansion, RTL)
- Empty, loading, and error state content
### Asset Delivery
- Icons (SVG, named per convention)
- Images (resolution, format, responsive variants)
- Fonts (files or service links)
- Any custom illustrations or graphics
### Edge Cases
- Minimum and maximum content scenarios
- Responsive behavior at each breakpoint
- Browser/device-specific considerations
- Accessibility requirements (ARIA, keyboard, screen reader)
### Implementation Notes
- Component reuse suggestions
- Data structure assumptions
- API dependencies
- Performance considerations

### Web Implementation Details
Include these platform-specific details in handoff documents to save developers debugging time:

**Interactivity:**
- Inputs should be wrapped in a `<form>` for Enter-to-submit; specify correct `type` attributes
- Input decorations (icons, prefixes) should be absolutely positioned with padding, not adjacent elements
- Buttons should disable after submission to prevent duplicate requests
- Dropdown menus should trigger on `mousedown`, not `click`
- Interactive elements should disable `user-select`; decorative overlays should disable `pointer-events`
- For nested menus, implement a "prediction cone" to prevent accidental close on pointer movement

**Touch & Mobile:**
- Gate hover states behind `@media (hover: hover)` — they should not appear on touch press
- Input font size must be at least 16px (prevents iOS zoom on focus)
- Do not auto-focus inputs on touch devices (keyboard covers screen)
- Add `muted` and `playsinline` to `<video>` tags for iOS autoplay
- Disable `touch-action` on custom pan/zoom gesture components
- Replace the default iOS tap highlight (`-webkit-tap-highlight-color: rgba(0,0,0,0)`) with an appropriate alternative

**Performance:**
- Avoid large `blur()` values on `filter`/`backdrop-filter` — they can be slow
- Use radial gradients instead of scaling and blurring filled rectangles (prevents banding)
- Toggle `will-change` only for the duration of unperformant scroll animations, not permanently
- Limit auto-playing videos on iOS; pause or unmount off-screen videos
- Use `transform: translateZ(0)` sparingly for GPU rendering of unperformant animations

**Data Patterns:**
- Optimistically update data locally and roll back on server error with user feedback
- Authentication redirects should happen server-side before the client loads to avoid janky URL changes
## Best Practices
- Use design tokens, not raw values
- Annotate behavior, not just appearance
- Include all states, not just the happy path
- Provide redlines for complex layouts
- Walk through the handoff with the developer
