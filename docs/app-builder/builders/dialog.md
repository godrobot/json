# Dialog Format Documentation

## Overview

The Dialog format defines the simplified input structure for creating dialogs (alert modals) in the Makyo App Builder. Dialogs are used for confirmations, alerts, and important messages that require user interaction.

---

## Simplified Input Structure

```typescript
interface AiDialogInput {
  name: string                      // Dialog name/identifier (required)
  headline: string                  // Dialog headline/title (required)
  headlineTypography?: string        // Typography for headline (optional)
  content: string                   // Dialog content/message (required)
  contentTypography?: string         // Typography for content (optional)
  showIcon?: boolean                // Whether to show icon (optional)
  icon?: string                     // Material icon name (optional)
  showDivider?: boolean             // Whether to show divider (optional)
  leadingButton?: {                 // Leading (left) button (optional)
    label: string
    color?: string
    enabled?: boolean
  }
  trailingButton?: {                // Trailing (right) button (optional)
    label: string
    color?: string
    enabled?: boolean
  }
  alignment?: {                     // Text alignment (optional)
    title?: 'start' | 'center' | 'end'
    content?: 'start' | 'center' | 'end'
    footer?: 'start' | 'center' | 'end'
    icon?: 'start' | 'center' | 'end'
  }
  width?: string                    // Width format (optional)
}
```

---

## Properties

### `name` (required)
The dialog name/identifier used internally and for referencing.

**Type:** `string`

**Example:**
```json
{
  "name": "Delete Confirmation"
}
```

---

### `headline` (required)
The main headline/title displayed at the top of the dialog.

**Type:** `string`

**Example:**
```json
{
  "headline": "Delete Item"
}
```

---

### `headlineTypography` (optional)
Typography variant for the headline text.

**Type:** `string`

**Default:** Empty string (uses default)

**Example:**
```json
{
  "headlineTypography": "Title Extra Small"
}
```

**See also:** [Typography Format](../format/styles/typography.md)

---

### `content` (required)
The main content/message displayed in the dialog body.

**Type:** `string`

**Example:**
```json
{
  "content": "Are you sure you want to delete this item? This action cannot be undone."
}
```

---

### `contentTypography` (optional)
Typography variant for the content text.

**Type:** `string`

**Default:** Empty string (uses default)

**Example:**
```json
{
  "contentTypography": "Body Large"
}
```

**See also:** [Typography Format](../format/styles/typography.md)

---

### `showIcon` (optional)
Whether to display an icon in the dialog header.

**Type:** `boolean`

**Default:** `true`

**Example:**
```json
{
  "showIcon": true
}
```

---

### `icon` (optional)
Material icon name displayed in the dialog header.

**Type:** `string`

**Default:** `"info"`

**Example:**
```json
{
  "icon": "warning"
}
```

**See also:** [Material Icons](https://fonts.google.com/icons)

---

### `showDivider` (optional)
Whether to show a divider line between header and content.

**Type:** `boolean`

**Default:** `false`

**Example:**
```json
{
  "showDivider": false
}
```

---

### `leadingButton` (optional)
Configuration for the leading (left/cancel) button.

**Properties:**
- `label`: Button text (default: `"Cancel"`)
- `color`: Color from brand kit (default: empty)
- `enabled`: Whether button is enabled (default: `true`)

**Example:**
```json
{
  "leadingButton": {
    "label": "Cancel",
    "color": "neutral-100",
    "enabled": true
  }
}
```

**See also:** [Colors Format](../format/styles/colors.md)

---

### `trailingButton` (optional)
Configuration for the trailing (right/confirm) button.

**Properties:**
- `label`: Button text (default: `"Confirm"`)
- `color`: Color from brand kit (default: empty)
- `enabled`: Whether button is enabled (default: `true`)

**Example:**
```json
{
  "trailingButton": {
    "label": "Delete",
    "color": "primary-50",
    "enabled": true
  }
}
```

**See also:** [Colors Format](../format/styles/colors.md)

---

### `alignment` (optional)
Controls text alignment for different parts of the dialog.

**Properties:**
- `title`: Alignment for headline (`'start'` | `'center'` | `'end'`)
- `content`: Alignment for content (`'start'` | `'center'` | `'end'`)
- `footer`: Alignment for footer/buttons (`'start'` | `'center'` | `'end'`)
- `icon`: Alignment for icon (`'start'` | `'center'` | `'end'`)

**Default:**
- `title`: `"center"`
- `content`: `"center"`
- `footer`: `"right"`
- `icon`: `"center"`

**Example:**
```json
{
  "alignment": {
    "title": "center",
    "content": "center",
    "footer": "right",
    "icon": "center"
  }
}
```

**See also:** [Alignments Format](../format/styles/alignments.md)

---

### `width` (optional)
Controls the width of the dialog. Supports responsive breakpoints.

**Type:** `string`

**Format:** `"w:<value>"` with responsive breakpoints

**Default:** 
- `phone`: `"90%"`
- `phone-landscape`: `"350px"`
- `tablet`: `"350px"`
- `tablet-landscape`: `"350px"`
- `desktop`: `"350px"`
- `tv`: `"350px"`

**Breakpoint prefixes:**
- `ph:` - phone
- `pl:` - phone-landscape
- `ta:` - tablet
- `tl:` - tablet-landscape
- `de:` - desktop
- `tv:` - tv

**Examples:**
```json
{
  "width": "w:325px"
}
```

```json
{
  "width": "w:325px ta:w:450px de:w:530px"
}
```

**See also:** [Sizing Format](../format/styles/sizing.md), [Breakpoints Format](../format/styles/breakpoints.md)

---

## Complete Example

```json
{
  "name": "Delete Confirmation",
  "headline": "Delete Item",
  "headlineTypography": "Title Extra Small",
  "content": "Are you sure you want to delete this item? This action cannot be undone.",
  "contentTypography": "Body Large",
  "showIcon": true,
  "icon": "warning",
  "showDivider": false,
  "leadingButton": {
    "label": "Cancel",
    "color": "neutral-100",
    "enabled": true
  },
  "trailingButton": {
    "label": "Delete",
    "color": "primary-50",
    "enabled": true
  },
  "alignment": {
    "title": "center",
    "content": "center",
    "footer": "right",
    "icon": "center"
  },
  "width": "w:325px ta:w:450px de:w:530px"
}
```

---

## Related Documentation

- [Typography Format](../format/styles/typography.md)
- [Colors Format](../format/styles/colors.md)
- [Sizing Format](../format/styles/sizing.md)
- [Alignments Format](../format/styles/alignments.md)
- [Breakpoints Format](../format/styles/breakpoints.md)

