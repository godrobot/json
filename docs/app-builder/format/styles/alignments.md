# Alignment System Documentation

## Overview

The Makyo alignment system provides precise control over positioning and text alignment across different UI elements. It supports responsive alignment configurations that adapt to various screen sizes using breakpoints.

---

## Alignment Types
- horizontal
- vertical
- text
- component

### Horizontal Alignment (`h:`)
Controls the horizontal positioning of elements within their container.

**Syntax:** `h:<value>`

**Available values:**
- `start` - Align to the left edge
- `center` - Center horizontally
- `end` - Align to the right edge
- `parent` - Follow the parent's alignment

**Example:** `h:center`

---

### Vertical Alignment (`v:`)
Controls the vertical positioning of elements within their container.

**Syntax:** `v:<value>`

**Available values:**
- `start` - Align to the top edge
- `center` - Center vertically
- `end` - Align to the bottom edge

**Example:** `v:start`

---

### Text Alignment (`t:`)
Controls the alignment of text content within text elements.

**Syntax:** `t:<value>`

**Available values:**
- `left` - Align text to the left
- `center` - Center text
- `right` - Align text to the right
- `justify` - Justify text (align to both edges)

**Example:** `t:justify`

---

### Component Alignment (`c:`)
Controls the alignment of components/children within their layout context.

**Syntax:** `c:<value>`

**Available values:**
- `start` - Align children to the starting position
- `center` - Center the children
- `end` - Align children to the ending position
- `parent` - Children follow the parent's alignment

**Example:** `c:center`

---

## Responsive Alignments

Alignments can be configured differently for each breakpoint by prefixing the alignment type with a [breakpoint](breakpoints.md) abbreviation.

### Syntax
```
<alignment> <breakpoint>:<alignment> <breakpoint>:<alignment>
```

---

## Examples

### Basic Usage

```typescript
// Horizontal alignment
alignment: "h:center"

// Vertical alignment
alignment: "v:start"

// Text alignment
alignment: "t:left"

// Component alignment
alignment: "c:end"
```

### Responsive Alignment

When you specify an alignment without a breakpoint prefix, it acts as the default value for **all breakpoints** unless explicitly overridden:

```typescript
// "h:center" applies to ALL breakpoints
alignment: "h:center"

// "h:center" applies to phone, phone-landscape, tablet-landscape, desktop, and tv
// Only tablet uses "h:start"
alignment: "h:center ta:h:start"

// Each specified breakpoint gets its own value
// Unspecified breakpoints (phone, tablet-landscape, tv) use "h:end"
alignment: "h:end pl:h:center ta:h:start de:h:center"

### Combining Multiple Alignments

```typescript
// Horizontal and vertical alignment
alignment: "h:center v:center"

// Text and component alignment
alignment: "t:center c:start"

// Responsive with multiple types
alignment: "h:start v:center pl:h:center pl:v:start ta:h:end"
```

---

## Common Use Cases

### Centering Elements

```typescript
// Center both horizontally and vertically
alignment: "h:center v:center"

// Center text
alignment: "t:center"
```

---

## Best Practices

1. **Define defaults first** - Set your base alignment without breakpoint prefixes; this applies to all unspecified breakpoints
2. **Override selectively** - Only specify breakpoint-specific alignments where you need different behavior
3. **Use semantic values** - Choose alignment values that make sense for your content structure
4. **Combine alignments thoughtfully** - Use multiple alignment types when needed (e.g., `h:center v:center`)
5. **Use `parent` alignment** - For matching parent alignment.

---

## Alignment Type Reference

| Prefix | Type | Purpose | Available Values |
|--------|------|---------|------------------|
| `h:` | Horizontal | Horizontal positioning | `start`, `center`, `end`, `parent` |
| `v:` | Vertical | Vertical positioning | `start`, `center`, `end` |
| `t:` | Text | Text content alignment | `left`, `center`, `right`, `justify` |
| `c:` | Component | Component layout alignment | `start`, `center`, `end`, `parent` |

---

## Notes

- **Space-separated values:** Multiple alignment configurations are separated by spaces
- **Order independence:** Breakpoint-specific alignments can be specified in any order