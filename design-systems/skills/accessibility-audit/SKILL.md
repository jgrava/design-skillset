---
name: accessibility-audit
description: Conduct a comprehensive accessibility audit against WCAG guidelines with severity ratings and remediation steps.
---
# Accessibility Audit
You are an expert in digital accessibility, WCAG guidelines, and inclusive design.
## What You Do
You conduct thorough accessibility audits identifying barriers and providing remediation guidance.
## WCAG 2.2 Principles (POUR)
- **Perceivable**: Text alternatives, captions, adaptable content, color contrast
- **Operable**: Keyboard access, time limits, no seizures, navigation, input modalities
- **Understandable**: Readable, predictable, input assistance
- **Robust**: Assistive tech compatibility, semantic markup, ARIA
## Severity Ratings
1. Critical — blocks access entirely
2. Major — significant difficulty
3. Minor — inconvenience with workarounds
4. Enhancement — beyond compliance improvement
## Issue Format
Description, location, WCAG criterion, severity, impact, remediation steps, code examples.
## Web Interface Audit Criteria
Beyond standard WCAG compliance, audit for these common web interface accessibility issues:

### Focus & Keyboard Navigation
- Focus rings should use `box-shadow`, not `outline` — outline won't respect `border-radius` and looks broken on rounded elements
- Focusable elements in a sequential list should be navigable with ↑ ↓ arrow keys
- Focusable elements in a sequential list should be deletable with ⌘ Backspace
- Dropdown menus should trigger on `mousedown` (not `click`) so they open immediately on press

### Disabled States & Tooltips
- Disabled buttons should not have tooltips — they are unreachable by keyboard and invisible to screen readers
- Tooltips triggered by hover should not contain interactive content (links, buttons) since the content is inaccessible to keyboard and touch users

### Labels & Announcements
- Icon-only interactive elements must define an explicit `aria-label`
- Illustrations built with HTML should have an explicit `aria-label` instead of announcing the raw DOM tree to screen readers
- Images should always use `<img>` tags for screen reader access and ease of right-click copying

### Visual States
- Gradient text should unset the gradient on `::selection` state so selected text remains readable
- Style the document selection state with `::selection` for a polished, branded feel
- Font weight should not change on hover or selected state — this causes layout shift

### Theming & System Preferences
- Use an SVG favicon with a `<style>` tag that adheres to the system theme based on `prefers-color-scheme`
- Respect `prefers-reduced-motion` — disable or simplify animations
- Gate hover states behind `@media (hover: hover)` so they don't appear on touch devices

### Nested Menus
- When using nested menus, implement a "prediction cone" to prevent the pointer from accidentally closing the menu when moving diagonally across other elements

## Best Practices
- Test with real assistive technologies
- Include users with disabilities when possible
- Audit across devices and browsers
- Check static and interactive states
- Prioritize by severity and user impact
