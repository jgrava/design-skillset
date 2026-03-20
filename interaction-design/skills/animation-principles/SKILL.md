---
name: animation-principles
description: Apply animation principles to UI motion for purposeful, polished interactions.
---
# Animation Principles
You are an expert in applying motion design principles to create purposeful UI animations.
## What You Do
You apply animation principles to make interfaces feel natural, guide attention, and communicate state changes.
## Core UI Animation Principles
### Easing
- Ease-out: decelerating (entering elements)
- Ease-in: accelerating (exiting elements)
- Ease-in-out: both (moving between positions)
- Linear: only for continuous animations (progress bars)
### Duration
- Micro (50-100ms): button states, toggles
- Short (150-250ms): tooltips, fades, small movements
- Medium (250-400ms): page transitions, modals
- Long (400-700ms): complex choreography
### Motion Principles
- **Purposeful**: every animation communicates something
- **Quick**: faster is almost always better in UI
- **Natural**: follow physics (acceleration, deceleration)
- **Choreographed**: related elements move in coordinated sequence
- **Interruptible**: animations can be cancelled mid-flight
## Animation Types
- **Entrance**: fade in, slide in, scale up
- **Exit**: fade out, slide out, scale down
- **Emphasis**: pulse, shake, bounce
- **Transition**: morph, crossfade, shared element
- **Loading**: skeleton shimmer, spinner, progress
## Stagger and Sequence
- Stagger related items by 30-50ms each
- Lead with the most important element
- Limit total sequence duration to under 700ms
- Use consistent direction for related movements
## Interaction Duration Threshold
For interactions that should feel immediate (button presses, toggles, hover feedback), animation duration should not exceed 200ms. The 250-400ms range is for transitions between distinct views (modals, page changes) where the user expects a spatial shift, not for micro-interactions.

## Proportional Scale Values
Animation scale values should be proportional to the trigger size — the goal is subtle reinforcement, not theatrical emphasis:
- **Dialogs**: Don't scale from 0 → 1. Instead, fade opacity and scale from ~0.8 → 1.
- **Buttons on press**: Don't scale from 1 → 0.8. Use ~0.96 or ~0.9.
- **Tooltips and popovers**: Fade and translate a small amount (4-8px), not slide across the screen.

## Reduce Animation for Frequent Actions
Actions that are frequent and low in novelty should avoid extraneous animations because they become irritating with repetition:
- Opening a right-click or context menu
- Adding or deleting items from a list
- Hovering trivial buttons

Reserve expressive animation for moments of delight or major state transitions.

## Theme Switching
Switching between light and dark themes should not trigger transitions and animations on elements. Disable transitions globally during the theme change (e.g., add a `no-transition` class to the root, swap the theme, then remove the class after a frame).

## Offscreen Behavior
Looping animations (spinners, background effects, decorative motion) should pause when not visible on the screen. This offloads CPU and GPU usage and prevents battery drain on mobile. Use `IntersectionObserver` to detect visibility.

## Smooth Scrolling
Use `scroll-behavior: smooth` for navigating to in-page anchors, with an appropriate `scroll-margin-top` or `scroll-padding-top` offset to account for fixed headers.

## Performance
- Toggle `will-change` on unperformant scroll animations only for the duration of the animation — setting it permanently consumes memory
- Use `transform: translateZ(0)` sparingly to promote elements to their own GPU layer
- Large `blur()` values on `filter` and `backdrop-filter` can be slow; test on target devices
- Scaling and blurring filled rectangles causes banding — use radial gradients instead

## Best Practices
- Support prefers-reduced-motion
- Don't animate for the sake of it
- Test on low-powered devices
- Keep animations under 400ms for responsive feel
- Use will-change or transform for performance
