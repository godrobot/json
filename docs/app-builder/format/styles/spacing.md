# Spacing System Documentation

## Overview

The Makyo spacing system controls the space around and within elements using padding and margin properties. It supports multiple units and allows responsive configurations across different breakpoints.

---

## Spacing Properties

### Padding
Controls the internal spacing within an element.

**Syntax:** `<direction>:<value><unit>`

**Available directions:**
- `p:` - All sides (padding)
- `pt:` - Top padding
- `pr:` - Right padding
- `pb:` - Bottom padding
- `pl:` - Left padding

**Available units:**
- `em` - Relative to element's font size
- `rem` - Relative to root font size
- `px` - Pixels (absolute units)
- `%` - Percentage (relative to parent)

**Examples:**
```typescript
spacing: "pt:20px"
spacing: "p:1rem"
spacing: "pl:10% pr:10%"
```

---

### Margin
Controls the external spacing outside an element.

**Syntax:** `<direction>:<value><unit>`

**Available directions:**
- `m:` - All sides (margin)
- `mt:` - Top margin
- `mr:` - Right margin
- `mb:` - Bottom margin
- `ml:` - Left margin

**Available units:**
- `em` - Relative to element's font size
- `rem` - Relative to root font size
- `px` - Pixels (absolute units)
- `%` - Percentage (relative to parent)

**Examples:**
```typescript
spacing: "mb:16px"
spacing: "m:2rem"
spacing: "mt:5%"
```

---

### Gap
Controls the spacing between child elements in a container.

**Syntax:** `gap:<value><unit>`

**Available units:**
- `em` - Relative to element's font size
- `rem` - Relative to root font size
- `px` - Pixels (absolute units)
- `%` - Percentage (relative to parent)

**Examples:**
```typescript
spacing: "gap:10px"
spacing: "gap:1rem"
spacing: "gap:2%"
```

---

## Responsive Spacing

Spacing can be configured differently for each [breakpoint](breakpoints.md) by prefixing properties with a breakpoint abbreviation.

**Syntax:**
```
<property> <breakpoint>:<property> <breakpoint>:<property>
```

**Examples:**
```typescript
// Different padding on different screens
spacing: "p:1rem ta:p:2rem de:p:3rem"

// Responsive margin
spacing: "mb:16px ta:mb:24px de:mb:32px"

// Responsive gap
spacing: "gap:10px ta:gap:16px de:gap:24px"

// Complex responsive configuration
spacing: "pt:20px pb:20px ta:pt:40px ta:pb:40px de:p:60px"

// Combined responsive padding, margin, and gap
spacing: "p:1rem mb:1rem gap:10px ta:p:2rem ta:mb:2rem ta:gap:16px de:p:3rem de:mb:3rem de:gap:24px"
```

---

## Spacing Reference

| Property | Syntax | Description |
|----------|--------|-------------|
| Padding (all) | `p:<value><unit>` | Internal spacing on all sides |
| Padding Top | `pt:<value><unit>` | Internal spacing on top |
| Padding Right | `pr:<value><unit>` | Internal spacing on right |
| Padding Bottom | `pb:<value><unit>` | Internal spacing on bottom |
| Padding Left | `pl:<value><unit>` | Internal spacing on left |
| Margin (all) | `m:<value><unit>` | External spacing on all sides |
| Margin Top | `mt:<value><unit>` | External spacing on top |
| Margin Right | `mr:<value><unit>` | External spacing on right |
| Margin Bottom | `mb:<value><unit>` | External spacing on bottom |
| Margin Left | `ml:<value><unit>` | External spacing on left |
| Gap | `gap:<value><unit>` | Spacing between child elements |

### Unit Reference

| Unit | Type | Description |
|------|------|-------------|
| `em` | Relative | Relative to element's font size |
| `rem` | Relative | Relative to root font size |
| `px` | Absolute | Fixed pixel units |
| `%` | Relative | Percentage of parent container |
