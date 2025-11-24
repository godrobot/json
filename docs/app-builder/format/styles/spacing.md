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

## Recommended Component Spacing

The following table provides recommended margin values for different component types. These values ensure consistent spacing and visual hierarchy throughout your application.

### Component Margin Recommendations

| Component | Element | Top | Right | Bottom | Left | Format String |
|-----------|---------|-----|-------|--------|------|---------------|
| Text | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Section | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Tabs | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Form | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Rich Text | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Button | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Icon | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Image | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Video | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Audio | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| List | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Cards | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Gallery | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Accordion | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Locations | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Shopping Cart | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Timeline | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Data Table | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Single Row Table | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Map | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Divider | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Linear Progress | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Circular Progress | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Pie Chart | Component | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Bar Chart | Component | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Login Form | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Menu | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Calendar | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Prompt | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Quantity | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Pricing | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Newsletter | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Alert | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Comments | Component Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |
| Rating | Margin | 8px | 16px | 8px | 16px | `mt:8px mr:16px mb:8px ml:16px` |

### Quick Reference

**Standard Component Margin:**
```typescript
margin: "mt:8px mr:16px mb:8px ml:16px"
```

**Shorthand (when all values are the same):**
```typescript
// For equal top/bottom and left/right
margin: "mt:8px mb:8px ml:16px mr:16px"
```

**Note:** These are recommended default values. You can adjust spacing based on your design requirements and use responsive breakpoints to customize spacing for different screen sizes.

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
