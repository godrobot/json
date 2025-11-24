# Section Variant Documentation

## Overview

The Makyo section variant system controls the positioning behavior of sections. Sections can be normal or sticky with configurable positioning and offset.

---

## Section Variants

### Normal
Regular section with default positioning.

**Syntax:** `normal`

**Example:**
```typescript
variant: "normal"
```

---

### Sticky
Sticky section that remains fixed during scroll.

**Syntax:** `sticky:<position>:<offset>`

**Properties:**
1. **Position** - `top` or `bottom` - Alignment edge
2. **Offset** - `0` to `100` - Distance from edge in pixels

**Examples:**
```typescript
// Sticky at top with no offset
variant: "sticky:top:0"

// Sticky at top with 20px offset
variant: "sticky:top:20"

// Sticky at bottom with 10px offset
variant: "sticky:bottom:10"

// Sticky at bottom with no offset
variant: "sticky:bottom:0"
```

---

## Responsive Section Variants

Section variants can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Syntax:**
```
<variant> <breakpoint>:<variant> <breakpoint>:<variant>
```

**Examples:**
```typescript
// Normal on mobile, sticky on desktop
variant: "normal de:sticky:top:0"

// Sticky at top on mobile, sticky at bottom on desktop
variant: "sticky:top:0 de:sticky:bottom:20"

// Different offsets across breakpoints
variant: "sticky:top:0 ta:sticky:top:10 de:sticky:top:20"

// Normal on mobile, sticky on tablet+
variant: "normal ta:sticky:top:0"
```

---

## Section Variant Reference

| Variant | Syntax | Description |
|---------|--------|-------------|
| Normal | `normal` | Regular section with default positioning |
| Sticky | `sticky:<position>:<offset>` | Fixed position section during scroll |

### Position Values

| Value | Description |
|-------|-------------|
| `top` | Aligned to top edge |
| `bottom` | Aligned to bottom edge |

### Offset Range

| Property | Range | Description |
|----------|-------|-------------|
| Offset | `0`-`100` | Distance from edge in pixels |
