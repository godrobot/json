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

// Vertical on mobile and tablet, horizontal on desktop
orientation: "v de:h"
```

---

## Orientation Reference

| Value | Description |
|-------|-------------|
| `h` | Horizontal (content flows left to right) |
| `v` | Vertical (content flows top to bottom) |
