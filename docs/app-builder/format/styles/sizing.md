# Sizing System Documentation

## Overview

The Makyo sizing system controls element dimensions using width and height properties. It supports both pixel and percentage units, and allows responsive configurations across different breakpoints.

---

## Sizing Properties

### Width
Controls the horizontal dimension of an element.

**Syntax:** `w:<value><unit>`

**Available units:**
- `px` - Pixels (absolute units)
- `%` - Percentage (relative to parent)

**Examples:**
```typescript
size: "w:200px"
size: "w:50%"
```

---

### Height
Controls the vertical dimension of an element.

**Syntax:** `h:<value><unit>`

**Available units:**
- `px` - Pixels (absolute units)
- `%` - Percentage (relative to parent)

**Examples:**
```typescript
size: "h:100px"
size: "h:75%"
```

---

## Responsive Sizing

Sizing can be configured differently for each [breakpoint](breakpoints.md) by prefixing properties with a breakpoint abbreviation.

**Syntax:**
```
<property> <breakpoint>:<property> <breakpoint>:<property>
```

**Examples:**
```typescript
// Fixed width in pixels
size: "w:300px"

// Relative width in percentage
size: "w:100%"

// Combined width and height
size: "w:400px h:300px"

// Full width and height
size: "w:100% h:100%"

// Default width, larger on desktop
size: "w:100% de:w:800px"

// Percentage on mobile, fixed on tablet
size: "w:100% ta:w:600px"

// Different heights across breakpoints
size: "h:200px ta:h:300px de:h:400px"

// Complete responsive configuration
size: "w:100% h:300px ta:w:600px ta:h:400px de:w:1000px de:h:500px"

// Responsive card
size: "w:100% h:250px ta:w:400px ta:h:350px"

// Fixed aspect ratio container
size: "w:100% h:56.25%"
```

---

## Sizing Reference

| Property | Syntax | Units | Description |
|----------|--------|-------|-------------|
| Width | `w:<value><unit>` | `px`, `%` | Horizontal dimension |
| Height | `h:<value><unit>` | `px`, `%` | Vertical dimension |

### Unit Reference

| Unit | Type | Description |
|------|------|-------------|
| `px` | Absolute | Fixed pixel dimensions |
| `%` | Relative | Percentage of parent container |
