---
name: design-qa-checklist
description: Create QA checklists for verifying design implementation accuracy.
---
# Design QA Checklist
You are an expert in creating systematic QA checklists for verifying design implementation.
## What You Do
You create checklists that help designers systematically verify that implementations match design specifications.
## QA Categories
### Visual Accuracy
- Colors match design tokens
- Typography matches specified styles
- Spacing and sizing match specs
- Border radius, shadows, opacity correct
- Icons are correct size and color
- Images are correct aspect ratio and quality
### Layout
- Grid alignment is correct
- Responsive behavior matches specs at each breakpoint
- Content reflows properly
- No unexpected overflow or clipping
- Minimum and maximum widths respected
### Interaction
- All states render correctly (default, hover, focus, active, disabled)
- Transitions and animations match specs
- Click/touch targets are adequate size (44px minimum)
- Keyboard navigation works in correct order
- Focus indicators are visible
- Clicking input labels focuses the corresponding input field
- Inputs are wrapped with a `<form>` to allow submission via Enter
- Inputs use the appropriate `type` attribute (`password`, `email`, etc.)
- Inputs disable `spellcheck` and `autocomplete` where appropriate
- Inputs use the `required` attribute for HTML form validation where appropriate
- Input prefix/suffix decorations (icons) are absolutely positioned over the input with padding, not placed adjacent, and trigger focus on the input when clicked
- Toggles take effect immediately without requiring a confirmation step
- Buttons are disabled after submission to prevent duplicate network requests
- Interactive elements disable `user-select` on inner content
- Decorative elements (glows, gradients) disable `pointer-events` to avoid hijacking events
- Dropdown menus trigger on `mousedown` (not `click`) for immediate response
- Focusable elements in sequential lists are navigable with arrow keys (↑ ↓)
- Hover states are gated behind `@media (hover: hover)` so they don't appear on touch press
### Content
- Real content fits the layout (no lorem ipsum in production)
- Truncation works as specified
- Empty states display correctly and prompt to create a new item (with optional templates)
- Error messages are correct and highlight the relevant input(s)
- Loading states appear as designed
- Feedback is displayed relative to its trigger (e.g., inline checkmark on successful copy, not a toast notification)
### Accessibility
- Screen reader announces correctly
- Color contrast meets WCAG AA
- Focus management works
- ARIA labels and roles are correct
- Reduced motion is respected
- Icon-only interactive elements have an explicit `aria-label`
- Disabled buttons do not have tooltips (they are inaccessible)
- Focus rings use `box-shadow`, not `outline` (outline won't respect border-radius)
- Tooltips triggered by hover do not contain interactive content
- Images use `<img>` tags (not CSS backgrounds) for screen reader access and right-click copying
- HTML-built illustrations have an explicit `aria-label` rather than exposing raw DOM to screen readers
- Gradient text unsets the gradient on `::selection` state
- The document selection state is styled with `::selection`
### Cross-Platform
- Works in required browsers
- Works on required devices
- Handles different text sizes (OS accessibility settings)
- Handles different screen densities

### Typography Rendering
- Fonts apply `-webkit-font-smoothing: antialiased` for legibility
- Fonts apply `text-rendering: optimizeLegibility`
- Fonts are subset based on content, alphabet, or relevant languages
- Font weight does not change on hover or selected state (prevents layout shift)
- No font weights below 400 are used
- Tabular figures (`font-variant-numeric: tabular-nums`) are used in tables, timers, and anywhere layout shift is undesirable
- iOS text resizing is prevented with `-webkit-text-size-adjust: 100%`

### Motion
- Animation durations do not exceed 200ms for interactions that should feel immediate
- Switching themes does not trigger transitions or animations on elements
- Looping animations pause when not visible on screen (offloads CPU/GPU)
- `scroll-behavior: smooth` is applied for in-page anchor navigation with an appropriate offset
- Animation scale values are proportional to trigger size (dialogs fade and scale from ~0.8, not 0; buttons scale to ~0.96, not 0.8)
- Frequent, low-novelty actions avoid extraneous animations (right-click menus, list add/remove, trivial button hovers)

### Touch & Mobile
- Input font size is at least 16px (prevents iOS zoom on focus)
- Inputs do not auto-focus on touch devices (avoids keyboard covering screen)
- `<video>` tags include `muted` and `playsinline` for iOS autoplay
- Custom pan/zoom components disable `touch-action` to prevent native interference
- Default iOS tap highlight is disabled with `-webkit-tap-highlight-color: rgba(0,0,0,0)` and replaced with an appropriate alternative

### Performance
- Large `blur()` values on `filter`/`backdrop-filter` are avoided or tested for performance
- Filled rectangles use radial gradients instead of scaled/blurred shapes (prevents banding)
- `will-change` is toggled only for the duration of unperformant scroll animations
- Auto-playing videos on iOS are limited; off-screen videos are paused or unmounted
## QA Process
1. Self-review by developer against checklist
2. Designer visual QA pass
3. File bugs with screenshots comparing design vs implementation
4. Prioritize bugs by severity
5. Verify fixes
## Best Practices
- QA against the design spec, not memory
- Test with real content and data
- Check edge cases, not just happy paths
- Use browser dev tools to verify exact values
- Document recurring issues for prevention
