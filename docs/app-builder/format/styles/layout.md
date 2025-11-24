# Layout System Documentation

## Overview

The Makyo layout system controls how content is arranged within containers using column-based layouts. It supports responsive configurations across different breakpoints.

---

## Columns

**Syntax:** `cols:<width>[:<width>...]`

**Available layouts:**

**Single column:**
- `cols:100` - Full width single column

**Two columns:**
- `cols:50:50` - Two equal half-width columns
- `cols:60:40` - 60/40 split
- `cols:40:60` - 40/60 split
- `cols:70:30` - 70/30 split
- `cols:30:70` - 30/70 split
- `cols:67:33` - 67/33 split (roughly 2:1)
- `cols:33:67` - 33/67 split (roughly 1:2)
- `cols:75:25` - 75/25 split
- `cols:25:75` - 25/75 split

**Three columns:**
- `cols:33:33:33` - Three equal columns

**Four columns:**
- `cols:25:25:25:25` - Four equal columns

**Examples:**
```typescript
// Single column
layout: "cols:100"

// Two equal columns
layout: "cols:50:50"

// Sidebar layout (70/30)
layout: "cols:70:30"

// Three equal columns
layout: "cols:33:33:33"

// Four equal columns
layout: "cols:25:25:25:25"
```

---

## Responsive Layout

Layout can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Syntax:**
```
<layout> <breakpoint>:<layout> <breakpoint>:<layout>
```

**Examples:**
```typescript
// Single column on mobile, two columns on tablet+
layout: "cols:100 ta:cols:50:50"

// Single column on mobile, sidebar on desktop
layout: "cols:100 de:cols:70:30"

// Two columns on mobile, three on tablet, four on desktop
layout: "cols:50:50 ta:cols:33:33:33 de:cols:25:25:25:25"

// Stacked on mobile, side-by-side on larger screens
layout: "cols:100 ta:cols:60:40 de:cols:50:50"
```

---

## Layout Reference

| Configuration | Description |
|---------------|-------------|
| `cols:100` | Full width single column |
| `cols:50:50` | Two equal columns |
| `cols:60:40` | 60/40 split columns |
| `cols:40:60` | 40/60 split columns |
| `cols:70:30` | 70/30 split columns |
| `cols:30:70` | 30/70 split columns |
| `cols:67:33` | 67/33 split columns |
| `cols:33:67` | 33/67 split columns |
| `cols:75:25` | 75/25 split columns |
| `cols:25:75` | 25/75 split columns |
| `cols:33:33:33` | Three equal columns |
| `cols:25:25:25:25` | Four equal columns |
