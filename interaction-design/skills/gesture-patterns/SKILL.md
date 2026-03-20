---
name: gesture-patterns
description: Design gesture-based interactions for touch and pointer devices.
---
# Gesture Patterns
You are an expert in designing intuitive gesture-based interactions.
## What You Do
You design gesture interactions that feel natural and discoverable across touch and pointer devices.
## Core Gestures
- **Tap**: Select, activate, toggle
- **Double tap**: Zoom, like/favorite
- **Long press**: Context menu, reorder mode, preview
- **Swipe**: Navigate, dismiss, reveal actions
- **Pinch**: Zoom in/out
- **Rotate**: Rotate content (maps, images)
- **Drag**: Move, reorder, adjust values
- **Pull**: Refresh content (pull-to-refresh)
## Gesture Design Rules
### Discoverability
- Pair gestures with visible affordances
- Provide visual hints on first use
- Always have a non-gesture alternative (button/menu)
### Feedback
- Immediate visual response when gesture starts
- Progress indication during gesture
- Threshold indicators (snap points, rubber-banding)
- Completion confirmation
### Thresholds
- Minimum distance before gesture activates (10-15px)
- Velocity thresholds for flick/swipe
- Direction lock (horizontal vs vertical)
- Cancel zone (return to start to abort)
## Conflict Resolution
- Scroll vs swipe: direction lock after initial movement
- Tap vs long press: time threshold (500ms typical)
- Pinch vs drag: number of touch points
- System gestures take priority (back swipe, notification pull)
## Accessibility
- Every gesture must have a non-gesture alternative
- Support switch control and voice control
- Custom gestures should be documented
- Respect reduced-motion preferences for gesture animations

## Touch Platform Implementation
These are platform-specific details that prevent common touch interaction bugs:

### Hover State Handling
- Gate all hover states behind `@media (hover: hover)` — on touch devices, hover states "stick" after a tap, which looks broken and confuses users

### iOS-Specific
- Input font size must be at least 16px — anything smaller causes iOS Safari to auto-zoom the viewport on focus, which is disorienting
- Do not auto-focus inputs on touch devices — the on-screen keyboard covers the screen and the user loses context
- Add `muted` and `playsinline` attributes to `<video>` tags to enable autoplay on iOS (without these, iOS blocks autoplay entirely)
- Disable the default iOS tap highlight with `-webkit-tap-highlight-color: rgba(0,0,0,0)`, but always replace it with a visible alternative (`:active` state, scale animation, or opacity change) so the user still gets feedback

### Custom Gesture Components
- Disable `touch-action` on elements that implement custom pan and zoom gestures — this prevents interference from native browser behaviors like zooming and scrolling that would fight with your gesture handling
## Best Practices
- Follow platform conventions
- Keep gestures simple (one or two fingers)
- Provide undo for destructive gesture actions
- Test with one-handed use
- Don't require precision timing
