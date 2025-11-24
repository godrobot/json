# Overlay Format Documentation

## Overview

The Overlay format defines the simplified input structure for creating overlays (modals/sheets) in the Makyo App Builder. Overlays are displayed on top of pages and can slide in from different directions with customizable sizes and shapes.

---

## Simplified Input Structure

```typescript
interface AiOverlayInput {
  title: string                    // Overlay title (required)
  icon?: string                    // Material icon name (optional)
  backgroundColor?: string          // Background color from brand kit (optional)
  components: AiComponentInput[]    // Array of component inputs (required)
  placement?: string              // Placement format (optional)
  size?: string                    // Size format (optional)
  shape?: string                   // Shape format (optional)
  closeBehavior?: 'direct' | 'back' // How overlay closes (optional)
  opacity?: number                 // Opacity 0-100 (optional)
}
```

---

## Properties

### `title` (required)
The overlay title displayed in the header.

**Type:** `string`

**Example:**
```json
{
  "title": "Add Article Query"
}
```

---

### `icon` (optional)
Material icon name for the overlay. Used in the overlay header.

**Type:** `string`

**Default:** `"draft"`

**Example:**
```json
{
  "icon": "post_add"
}
```

**See also:** [Material Icons](https://fonts.google.com/icons)

---

### `backgroundColor` (optional)
Background color from the brand kit color scheme.

**Type:** `string`

**Default:** `"primary-95"`

**Example:**
```json
{
  "backgroundColor": "primary-90"
}
```

**See also:** [Colors Format](../format/styles/colors.md)

---

### `components` (required)
Array of component inputs that make up the overlay content.

**Type:** `AiComponentInput[]`

**Example:**
```json
{
  "components": [
    {
      "type": "form",
      "children": [
        {
          "type": "text-field",
          "title": "Name"
        }
      ]
    }
  ]
}
```

**See also:** [Component Parser Workflow](../component-parser-workflow.md)

---

### `placement` (optional)
Controls where the overlay appears on screen. Supports responsive breakpoints.

**Type:** `string`

**Format:** `"<default> <breakpoint>:<value>"`

**Values:** `"top"` | `"bottom"` | `"left"` | `"right"`

**Default:** `"bottom"` for all breakpoints

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
  "placement": "bottom"
}
```

```json
{
  "placement": "bottom ta:left de:left"
}
```

**See also:** [Breakpoints Format](../format/styles/breakpoints.md)

---

### `size` (optional)
Controls the size of the overlay. Supports responsive breakpoints.

**Type:** `string`

**Format:** `"w:<value>"` or `"<value>"` with responsive breakpoints

**Default:** `"100%"` for all breakpoints

**Examples:**
```json
{
  "size": "w:90%"
}
```

```json
{
  "size": "w:90% ta:w:50% de:w:40%"
}
```

**See also:** [Sizing Format](../format/styles/sizing.md)

---

### `shape` (optional)
Controls the corner radius/shape of the overlay. Supports responsive breakpoints.

**Type:** `string`

**Values:** `"none"` | `"small"` | `"medium"` | `"large"`

**Default:** `"medium"` for all breakpoints

**Examples:**
```json
{
  "shape": "medium"
}
```

```json
{
  "shape": "medium ta:large"
}
```

**See also:** [Corner Radius Format](../format/styles/corner-radius.md)

---

### `closeBehavior` (optional)
Controls how the overlay closes when the user interacts with it.

**Type:** `"direct"` | `"back"`

**Default:** `"direct"`

- `"direct"`: Closes immediately when close button is clicked
- `"back"`: Requires back button press or swipe gesture

**Example:**
```json
{
  "closeBehavior": "direct"
}
```

---

### `opacity` (optional)
Controls the opacity of the overlay background (0-100).

**Type:** `number`

**Default:** `100` (fully opaque)

**Example:**
```json
{
  "opacity": 85
}
```

---

## Complete Example

```json
{
  "title": "Add Article Query",
  "icon": "post_add",
  "backgroundColor": "primary-90",
  "placement": "bottom ta:left de:left",
  "size": "w:90% ta:w:50% de:w:40%",
  "shape": "medium",
  "closeBehavior": "direct",
  "opacity": 85,
  "components": [
    {
      "type": "form",
      "children": [
        {
          "type": "text-field",
          "title": "Title"
        },
        {
          "type": "button",
          "label": "Submit"
        }
      ]
    }
  ]
}
```

---

## Related Documentation

- [Component Parser Workflow](../component-parser-workflow.md)
- [Colors Format](../format/styles/colors.md)
- [Sizing Format](../format/styles/sizing.md)
- [Corner Radius Format](../format/styles/corner-radius.md)
- [Breakpoints Format](../format/styles/breakpoints.md)

