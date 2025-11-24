# Aspect Ratio Documentation

## Overview

The Makyo aspect ratio system controls the proportional relationship between width and height of elements. It supports responsive configurations across different breakpoints.

---

## Aspect Ratio

**Syntax:** `<value>`

**Available values:**
- `auto` - Auto (natural dimensions)
- `1-1` - Square
- `4-3` - Standard
- `16-9` - Widescreen
- `3-2` - 35mm Film
- `5-4` - Large Format
- `7-5` - Traditional Print
- `8-10` - Common Print
- `9-16` - Vertical
- `2-1` - Panoramic
- `21-9` - Ultra-wide

**Examples:**
```typescript
aspect: "auto"
aspect: "1-1"
aspect: "16-9"
aspect: "9-16"
aspect: "21-9"
```

---

## Responsive Aspect Ratio

Aspect ratio can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Syntax:**
```
<value> <breakpoint>:<value> <breakpoint>:<value>
```

**Examples:**
```typescript
// Square on mobile, widescreen on desktop
aspect: "1-1 de:16-9"

// Vertical on mobile, horizontal on tablet+
aspect: "9-16 ta:16-9"

// Different ratios across breakpoints
aspect: "4-3 ta:16-9 de:21-9"

// Auto on mobile, fixed ratio on larger screens
aspect: "auto ta:16-9"
```

---

## Aspect Ratio Reference

| Value | Ratio | Description |
|-------|-------|-------------|
| `auto` | Auto | Natural dimensions |
| `1-1` | 1:1 | Square |
| `4-3` | 4:3 | Standard |
| `16-9` | 16:9 | Widescreen |
| `3-2` | 3:2 | 35mm Film |
| `5-4` | 5:4 | Large Format |
| `7-5` | 7:5 | Traditional Print |
| `8-10` | 8:10 | Common Print |
| `9-16` | 9:16 | Vertical |
| `2-1` | 2:1 | Panoramic |
| `21-9` | 21:9 | Ultra-wide |
