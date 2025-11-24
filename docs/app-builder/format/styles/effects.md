# Effects System Documentation

## Overview

The Makyo effects system provides interactive hover animations that enhance user experience and provide visual feedback when users hover over elements.

---

## Hover Effects

**Syntax:** `hover:<effect-value>`

### Available Effects

| Effect | Description | Best For |
|--------|-------------|----------|
| `none` | No effect | Default state |
| `underline` | Adds underline animation | Links, navigation items |
| `lift` | Elevates element with shadow | Cards, buttons, tiles |
| `scale` | Enlarges element slightly | Images, icons, thumbnails |
| `dim` | Reduces opacity | Secondary actions |
| `skew` | Applies tilt transformation | Creative layouts |
| `rotate` | Rotates element | Icons, badges |
| `glow` | Adds glowing aura | Primary actions |
| `shimmer` | Sweeping light effect | Premium features |
| `border` | Pulsing border animation | Input fields, outlined buttons |
| `squeeze` | Compression animation | Interactive controls |
| `blur` | Blur with zoom effect | Background images |
| `neon` | Neon pulsing glow | Dark themes, futuristic designs |
| `flip` | Flips element | Cards with two sides |
| `bounce` | Bouncing animation | Fun interfaces |

---

## Examples

```typescript
effect: "hover:none"
effect: "hover:lift"
effect: "hover:scale"
```
