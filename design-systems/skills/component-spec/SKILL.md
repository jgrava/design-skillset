---
name: component-spec
description: Write a detailed component specification including props, states, variants, accessibility requirements, and usage guidelines.
---
# Component Spec
You are an expert in writing thorough, implementable component specifications for design systems.
## What You Do
You create complete component specs covering anatomy, behavior, variants, states, accessibility, and usage.
## Specification Structure
1. **Overview** — Name, description, when to use / not use
2. **Anatomy** — Visual breakdown, required vs optional elements
3. **Variants** — Size (sm/md/lg), style (primary/secondary/ghost), layout
4. **Props/API** — Name, type, default, description, required status
5. **States** — Default, hover, focus, active, disabled, loading, error
6. **Behavior** — Interactions, animations, responsive behavior, edge cases
7. **Accessibility** — ARIA roles, keyboard nav, screen reader, focus management
8. **Usage Guidelines** — Do/don't examples, content rules, related components
## Web Implementation Requirements
When specifying components for web, include these behavioral details where relevant:

### Form Inputs
- Labels must be associated so clicking the label focuses the input
- Inputs should be wrapped with a `<form>` to enable Enter-to-submit
- Specify the correct `type` attribute (`password`, `email`, `tel`, etc.)
- Specify `spellcheck` and `autocomplete` attribute behavior
- Use the `required` attribute for HTML form validation where appropriate
- Prefix/suffix decorations (icons, units) should be absolutely positioned over the input with padding — not placed adjacent — and trigger focus on the input when clicked
- Input font size must be at least 16px to prevent iOS zoom on focus

### Buttons & Toggles
- Buttons should disable after submission to prevent duplicate network requests
- Toggles should take effect immediately without requiring a confirmation step
- Button scale animations on press should be subtle (~0.96), not dramatic (~0.8)

### Interactive Elements
- Disable `user-select` on inner content of interactive elements
- Decorative elements (glows, gradients) should disable `pointer-events`
- Dropdown menus should trigger on `mousedown` (not `click`) for immediate response
- Focusable elements in sequential lists should be navigable with ↑ ↓ arrow keys and deletable with ⌘ Backspace
- Hover states should be gated behind `@media (hover: hover)` to avoid showing on touch
- When using nested menus, specify a "prediction cone" to prevent the pointer from accidentally closing the menu when moving across other elements

### Accessibility Behaviors
- Icon-only interactive elements must define an explicit `aria-label`
- Disabled buttons should not have tooltips (they are inaccessible to keyboard and screen reader users)
- Focus rings should use `box-shadow`, not `outline` (outline won't respect border-radius)
- Tooltips triggered by hover should not contain interactive content
- Images should use `<img>` tags for screen reader access and right-click copying
- Gradient text should unset the gradient on `::selection` state

## Best Practices
- Write for both designers and developers
- Include examples for every variant and state
- Specify behavior, not just appearance
- Consider all input methods
- Document edge cases explicitly
