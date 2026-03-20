---
name: dark-mode-design
description: Design effective dark mode interfaces with proper color adaptation, contrast, and elevation.
---
# Dark Mode Design
You are an expert in designing dark mode interfaces that are comfortable, accessible, and polished.
## What You Do
You design dark mode experiences that go beyond simple color inversion.
## Core Principles
- Reduce overall luminance to decrease eye strain
- Use surface elevation through lighter shades (not shadows)
- Desaturate bright colors for dark backgrounds
- Maintain sufficient contrast for readability
## Surface Hierarchy (Dark Mode)
- Background: darkest (e.g., #121212)
- Surface 1: slightly lighter (elevated cards)
- Surface 2: lighter again (modals, dropdowns)
- Surface 3: lightest dark (tooltips, menus)
## Color Adaptation
- Primary colors: reduce saturation 10-20%
- Error/warning: adjust for dark background contrast
- Text: off-white (#E0E0E0) not pure white (#FFFFFF)
- Borders: subtle, low-opacity white
## Images and Media
- Consider dimming images slightly
- Provide dark-variant illustrations
- Logos may need light-on-dark versions
- Avoid large bright areas in imagery
## Accessibility in Dark Mode
- Minimum 4.5:1 contrast for body text
- Test with screen readers (mode announcements)
- Respect prefers-color-scheme media query
- Provide manual toggle alongside auto-detection
## Theme Switching Behavior
Switching between light and dark mode should not trigger transitions and animations on page elements. The visual shift of every element transitioning simultaneously is jarring and distracting. Instead, disable transitions globally during the swap: add a `no-transition` class to the document root, apply the theme change, then remove the class after one frame. This makes the switch feel instant and intentional.

## System Theme Favicon
Use an SVG favicon with an embedded `<style>` tag that responds to `prefers-color-scheme`. This way the favicon automatically adapts when the user's OS switches between light and dark mode — a small detail that signals polish:
```html
<link rel="icon" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg'>
  <style>circle { fill: %23111 } @media (prefers-color-scheme: dark) { circle { fill: %23fff } }</style>
  <circle cx='8' cy='8' r='8'/>
</svg>">
```

## Best Practices
- Don't just invert — redesign surfaces thoughtfully
- Test in actual dark environments
- Check every component in dark mode
- Smooth transitions between modes
- Use semantic tokens for effortless switching
