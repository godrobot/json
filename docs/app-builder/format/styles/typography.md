# Typography System Documentation

## Overview

The Makyo typography system controls text styling using predefined variants or custom configurations. It supports responsive configurations across different breakpoints.

---

## Typography Variants

### Predefined Variants
Use predefined typography styles following a design system scale.

**Syntax:** `<variant-name>`

**Available variants:**
- **Display:** `display-extra-extra-large`, `display-extra-large`, `display-large`, `display-medium`, `display-small`, `display-extra-small`, `display-extra-extra-small`
- **Headline:** `headline-extra-extra-large`, `headline-extra-large`, `headline-large`, `headline-medium`, `headline-small`, `headline-extra-small`, `headline-extra-extra-small`
- **Title:** `title-extra-extra-large`, `title-extra-large`, `title-large`, `title-medium`, `title-small`, `title-extra-small`, `title-extra-extra-small`
- **Body:** `body-extra-extra-large`, `body-extra-large`, `body-large`, `body-medium`, `body-small`, `body-extra-small`, `body-extra-extra-small`
- **Label:** `label-extra-extra-large`, `label-extra-large`, `label-large`, `label-medium`, `label-small`, `label-extra-small`, `label-extra-extra-small`

**Examples:**
```typescript
typography: "body-large"
typography: "headline-medium"
typography: "display-large"
typography: "label-small"
```

---

### Custom Typography
Define custom typography with specific properties.

**Syntax:** `custom:<family>:<style>:<size>:<line-height>:<letter-spacing>:<transform>`

**Properties (in order):**
1. **Family** - `<font-name>` - Google Fonts
2. **Style** - `100`, `200`, `300`, `regular`, `500`, `600`, `700`, `800`, `900`, `italic`, `100italic`-`900italic`
3. **Size** - `<value>px` - Font size in pixels (8-100)
4. **Line Height** - `<value>` - Unitless multiplier (0-10)
5. **Letter Spacing** - `<value>px` - Character spacing (-5px to 5px)
6. **Transform** - `none`, `uppercase`, `lowercase`, `capitalize`

**Omitting properties:** Leave the position empty to use default values.

**Examples:**
```typescript
// All properties defined
typography: "custom:Roboto:600:18px:1.5:0.5px:none"

// Only family and size
typography: "custom:Inter::16px:::"

// Family, style, and size
typography: "custom:Open Sans:700:24px::"

// Size and line height only
typography: "custom:::20px:1.6::"

// With text transform
typography: "custom:Montserrat:700:18px:::uppercase"
```

---

## Responsive Typography

Typography can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Syntax:**
```
<typography> <breakpoint>:<typography> <breakpoint>:<typography>
```

**Examples:**
```typescript
// Responsive variants
typography: "body-medium ta:body-large de:body-extra-large"

// Predefined on mobile, custom on larger screens
typography: "body-medium ta:custom:Roboto:600:18px::"

// Different custom configurations
typography: "custom:Inter::14px:: ta:custom:Inter::16px:: de:custom:Inter:600:18px::"

// Complex responsive with transforms
typography: "headline-small ta:custom:Montserrat:700:24px:::uppercase de:custom:Montserrat:700:32px:::uppercase"
```

---

## Typography Reference

### Variant Types

| Type | Syntax | Description |
|------|--------|-------------|
| Predefined | `<variant-name>` | Use design system variants |
| Custom | `custom:<family>:<style>:<size>:<line-height>:<letter-spacing>:<transform>` | Define custom typography |

### Custom Properties

| Position | Property | Values | Description |
|----------|----------|--------|-------------|
| 1 | Font Family | `<font-name>` | Google Fonts |
| 2 | Font Style | `100`-`900`, `regular`, `italic`, etc. | Font weight and style |
| 3 | Font Size | `<value>px` | Text size in pixels (8-100) |
| 4 | Line Height | `<value>` | Vertical line spacing (0-10) |
| 5 | Letter Spacing | `<value>px` | Character spacing (-5px to 5px) |
| 6 | Text Transform | `none`, `uppercase`, `lowercase`, `capitalize` | Text casing transformation |
