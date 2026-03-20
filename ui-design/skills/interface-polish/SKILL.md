---
name: interface-polish
description: Apply web interface polish guidelines covering interactivity, typography rendering, motion, touch, performance, and accessibility details that separate a functional interface from a crafted one. Use this skill as a final-pass checklist when reviewing or specifying any web interface, or when a designer or developer asks about implementation-level quality details.
---
# Interface Polish

You are an expert in the craft details that make web interfaces feel polished, responsive, and professional. This skill covers the implementation-level decisions that sit between design specs and shipped product — the details that users feel but rarely articulate.

## When to Use This Skill
Use this as a final-pass review or as a reference when specifying web interfaces. These guidelines apply broadly to all web projects and complement component specs, handoff docs, and QA checklists with concrete implementation details.

## Interactivity

### Form Inputs
- Clicking the input label should focus the input field (use associated `<label>` elements)
- Inputs should be wrapped with a `<form>` to submit by pressing Enter
- Inputs should have an appropriate `type` like `password`, `email`, `tel`, etc.
- Inputs should disable `spellcheck` and `autocomplete` attributes most of the time
- Inputs should leverage HTML form validation by using the `required` attribute when appropriate
- Input prefix and suffix decorations (such as icons or units) should be absolutely positioned on top of the text input with padding, not placed next to it, and should trigger focus on the input when clicked

### Buttons & Toggles
- Toggles should immediately take effect, not require confirmation
- Buttons should be disabled after submission to avoid duplicate network requests

### General Interactive Elements
- Interactive elements should disable `user-select` for inner content
- Decorative elements (glows, gradients) should disable `pointer-events` to not hijack events
- There should be no dead areas between interactive elements in a vertical or horizontal list — increase their `padding` to fill the gaps

## Typography Rendering
- Fonts should have `-webkit-font-smoothing: antialiased` applied for better legibility
- Fonts should have `text-rendering: optimizeLegibility` applied for better legibility
- Fonts should be subset based on the content, alphabet, or relevant languages
- Font weight should not change on hover or selected state to prevent layout shift
- Font weights below 400 should not be used
- Medium-sized headings generally look best with a font weight between 500-600
- Adjust values fluidly by using CSS `clamp()`, e.g. `clamp(48px, 5vw, 72px)` for heading `font-size`
- Where available, tabular figures should be applied with `font-variant-numeric: tabular-nums`, particularly in tables or when layout shifts are undesirable (timers, counters)
- Prevent text resizing unexpectedly in landscape mode on iOS with `-webkit-text-size-adjust: 100%`

## Motion
- Switching themes should not trigger transitions and animations on elements
- Animation duration should not be more than 200ms for interactions to feel immediate
- Animation values should be proportional to the trigger size:
  - Don't animate dialog scale in from 0 → 1, fade opacity and scale from ~0.8
  - Don't scale buttons on press from 1 → 0.8, but ~0.96 or ~0.9
- Actions that are frequent and low in novelty should avoid extraneous animations:
  - Opening a right-click menu
  - Deleting or adding items from a list
  - Hovering trivial buttons
- Looping animations should pause when not visible on the screen to offload CPU and GPU usage
- Use `scroll-behavior: smooth` for navigating to in-page anchors, with an appropriate offset

## Touch
- Hover states should not be visible on touch press, use `@media (hover: hover)`
- Font size for inputs should not be smaller than 16px to prevent iOS zooming on focus
- Inputs should not auto-focus on touch devices as it will open the keyboard and cover the screen
- Apply `muted` and `playsinline` to `<video>` tags to auto play on iOS
- Disable `touch-action` for custom components that implement pan and zoom gestures to prevent interference from native behavior like zooming and scrolling
- Disable the default iOS tap highlight with `-webkit-tap-highlight-color: rgba(0,0,0,0)`, but always replace it with an appropriate alternative

## Performance Optimizations
- Large `blur()` values for `filter` and `backdrop-filter` may be slow
- Scaling and blurring filled rectangles will cause banding — use radial gradients instead
- Sparingly enable GPU rendering with `transform: translateZ(0)` for unperformant animations
- Toggle `will-change` on unperformant scroll animations for the duration of the animation only — don't leave it on permanently
- Auto-playing too many videos on iOS will choke the device — pause or even unmount off-screen videos
- Detect and adapt to the hardware and network capabilities of the user's device

## Accessibility Details
- Disabled buttons should not have tooltips — they are not accessible
- Box shadow should be used for focus rings, not outline which won't respect border-radius
- Focusable elements in a sequential list should be navigable with ↑ ↓
- Focusable elements in a sequential list should be deletable with ⌘ Backspace
- To open immediately on press, dropdown menus should trigger on `mousedown`, not `click`
- Use an SVG favicon with a style tag that adheres to the system theme based on `prefers-color-scheme`
- Icon-only interactive elements should define an explicit `aria-label`
- Tooltips triggered by hover should not contain interactive content
- Images should always be rendered with `<img>` for screen readers and ease of copying from the right-click menu
- Illustrations built with HTML should have an explicit `aria-label` instead of announcing the raw DOM tree
- Gradient text should unset the gradient on `::selection` state
- When using nested menus, use a "prediction cone" to prevent the pointer from accidentally closing the menu when moving across other elements

## Design Patterns
- Optimistically update data locally and roll back on server error with feedback
- Authentication redirects should happen on the server before the client loads to avoid janky URL changes
- Style the document selection state with `::selection`
- Display feedback relative to its trigger:
  - Show a temporary inline checkmark on a successful copy, not a notification
  - Highlight the relevant input(s) on form error(s)
- Empty states should prompt to create a new item, with optional templates
