# Border System Documentation

## Overview

The Makyo border system provides comprehensive control over element borders, including individual border sides, widths, styles, and corner radius configurations. It supports responsive border configurations that adapt to various screen sizes using breakpoints.

---

## Border Properties

### Show Border (`show:`)
Controls which sides of an element have visible borders.

**Syntax:** `show:<side>[,<side>...]`

**Available sides:**
- `top` - Top border
- `inline-end` - Right border (respects RTL)
- `bottom` - Bottom border
- `inline-start` - Left border (respects RTL)

**Examples:**
```typescript
// Single side
border: "show:top"

// Multiple sides (comma-separated)
border: "show:top,bottom"

// All sides
border: "show:top,inline-end,bottom,inline-start"
```

---

### Border Width (`width:`)
Controls the thickness of the border in pixels.

**Syntax:** `width:<value>`

**Range:** `0` to `25` pixels

**Example:** `width:2`

---

### Border Style (`style:`)
Controls the visual style of the border line.

**Syntax:** `style:<value>`

**Available styles:**
- `solid` - Continuous solid line
- `dotted` - Series of dots
- `dashed` - Series of dashes

**Example:** `style:dashed`

---

### Corner Radius (`radius:`)
Controls the roundness of element corners.

**Syntax:** `radius:<value>`

**Available values:**
- `none` - No rounding (sharp corners)
- `extra-small` - Minimal rounding
- `small` - Subtle rounding
- `medium` - Moderate rounding
- `large` - Pronounced rounding
- `extra-large` - Very rounded corners
- `full` - Fully rounded (pill shape)

**Example:** `radius:medium`

---

## Examples

## Examples

### Basic Usage

```typescript
// Simple border on all sides
border: "show:top,inline-end,bottom,inline-start width:1 style:solid"

// Top border only
border: "show:top width:2 style:solid"

// Rounded corners with border
border: "show:top,inline-end,bottom,inline-start width:1 style:solid radius:medium"
```

### Border Styles

```typescript
// Solid border
border: "show:top,bottom width:1 style:solid"

// Dashed border
border: "show:top,inline-end,bottom,inline-start width:2 style:dashed"

// Dotted border
border: "show:bottom width:1 style:dotted"
```

### Corner Radius Variations

```typescript
// No radius (sharp corners)
border: "show:top,inline-end,bottom,inline-start width:1 style:solid radius:none"

// Subtle rounding
border: "show:top,inline-end,bottom,inline-start width:1 style:solid radius:small"

// Pill shape (fully rounded)
border: "show:top,inline-end,bottom,inline-start width:2 style:solid radius:full"
```

### Combining Multiple Properties

```typescript
// Card with bottom border and rounded corners
border: "show:bottom width:2 style:solid radius:medium"

// Button with full border and pill shape
border: "show:top,inline-end,bottom,inline-start width:2 style:solid radius:full"

// Divider with dashed top border
border: "show:top width:1 style:dashed"

// Multiple sides with different styles
border: "show:top,bottom width:1 style:solid radius:small"
```

---

## Border Property Reference

| Property | Syntax | Values | Description |
|----------|--------|--------|-------------|
| Show Border | `show:<sides>` | `top`, `inline-end`, `bottom`, `inline-start` | Controls which sides have borders |
| Width | `width:<value>` | `0-25` | Border thickness in pixels |
| Style | `style:<value>` | `solid`, `dotted`, `dashed` | Border line style |
| Radius | `radius:<value>` | `none`, `extra-small`, `small`, `medium`, `large`, `extra-large`, `full` | Corner roundness |

---

## Notes

- **Space-separated values:** Multiple border properties are separated by spaces
- **Comma-separated sides:** When specifying multiple border sides in `show:`, separate them with commas (no spaces)
- **Border colors:** Border colors are controlled separately through the component's color system, not within the border configuration

### Complete Border Configuration

A complete border configuration includes all properties:

```typescript
border: "show:top,inline-end,bottom,inline-start width:2 style:solid radius:medium"
```

With all variations:

```typescript
// Minimal configuration
border: "show:top width:1 style:solid"

// Full configuration with all properties
border: "show:top,inline-end,bottom,inline-start width:3 style:dashed radius:large"
```
