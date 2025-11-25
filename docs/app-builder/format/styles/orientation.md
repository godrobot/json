# Orientation Documentation

## Overview

The Makyo orientation system controls the directional flow of content within containers. It supports responsive configurations across different breakpoints.

---

## Orientation

**Syntax:** `<value>`

**Available values:**
- `h` - Horizontal (content flows left to right)
- `v` - Vertical (content flows top to bottom)

**Examples:**
```typescript
orientation: "h"
orientation: "v"
```

---

## Responsive Orientation

Orientation can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Available breakpoint prefixes:**
- `ph` - Phone
- `pl` - Phone Landscape
- `ta` - Tablet
- `tl` - Tablet Landscape
- `de` - Desktop
- `tv` - TV

**Syntax:**
```
<value> <breakpoint>:<value> <breakpoint>:<value>
```

**Examples:**
```typescript
// Vertical on mobile, horizontal on desktop
orientation: "v de:h"

// Horizontal on mobile, vertical on tablet+
orientation: "h ta:v"

// Vertical on phone, horizontal on phone landscape and above
orientation: "v pl:h"

// Vertical on phone and tablet, horizontal on desktop and TV
orientation: "v de:h tv:h"

// Different orientation for each breakpoint
orientation: "v pl:h ta:v tl:h de:v tv:h"

// Horizontal by default, vertical on tablet landscape and desktop
orientation: "h tl:v de:v"

// Complete example with all breakpoints
orientation: "v ph:v pl:h ta:v tl:h de:v tv:h"
```

---

## Orientation Reference

| Value | Description |
|-------|-------------|
| `h` | Horizontal (content flows left to right) |
| `v` | Vertical (content flows top to bottom) |
