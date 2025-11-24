# Component Format Documentation

## Overview

The Component format defines the simplified input structure for creating components in the Makyo App Builder. Components are the building blocks that can be used within:

- **Pages** - Main application screens
- **Overlays** - Modal overlays and sheets
- **Globals** - Global components shared across the app (future)

Each component has a specific type and can contain nested children components. Components cannot exist standalone - they must be part of a page, overlay, or global settings.

---

## Base Component Structure

All components share a common base structure:

```typescript
interface BaseAiComponentInput {
  type: string // Component type (required)
  id?: string // Optional custom ID
  title?: string // Optional title for the component body (_Title field)
  children?: AiComponentInput[] // Nested children (for container components)
}
```

**Note:** The `title` property is used for the component body's `_Title` field, not for component-specific titles. Many components have their own title properties (e.g., `compTitle` for forms, `imageTitle` for images, `alertTitle` for alerts).

---

## Component Types

Components are organized into groups. Each component has detailed specifications with all available properties and their formats.

### Container Components

- [`section`](../components/container/section.yaml) - Layout container with orientation, padding, gap, background
- [`tabs`](../components/container/tabs.yaml) - Tabbed interface with multiple tab panels
- [`form`](../components/container/form.yaml) - Form container with fields and submit button

### Text Components

- [`text`](../components/text/text.yaml) - Simple text display
- [`rich-text`](../components/text/rich-text.yaml) - Rich text with markdown/HTML support

### Button Components

- [`button`](../components/button/button.yaml) - Standard button with label and actions
- [`fab`](../components/button/fab.yaml) - Floating action button
- [`icon`](../components/button/icon.yaml) - Icon button

### Media Components

- [`image`](../components/media/image.yaml) - Image display
- [`video`](../components/media/video.yaml) - Video player
- [`audio`](../components/media/audio.yaml) - Audio player

### List Components

- [`list`](../components/list/list.yaml) - Simple list with data source
- [`card`](../components/list/card.yaml) - Card-based list
- [`gallery`](../components/list/gallery.yaml) - Image gallery
- [`accordion`](../components/list/accordion.yaml) - Expandable accordion list
- [`timeline`](../components/list/timeline.yaml) - Timeline display
- [`shopping-cart`](../components/list/shopping-cart.yaml) - Shopping cart component

### Table Components

- [`data-table`](../components/table/data-table.yaml) - Full-featured data table
- [`data-list`](../components/table/single-row.yaml) - Single row data list

### Form Field Components

- [`text-field`](../components/form/text-field.yaml) - Text input field
- [`checkbox`](../components/form/checkbox.yaml) - Checkbox input
- [`switch`](../components/form/switch.yaml) - Toggle switch
- [`selection`](../components/form/selection.yaml) - Single select dropdown
- [`slider`](../components/form/slider.yaml) - Range slider

**Note:** Additional form fields like `datetime-picker`, `file`, `image-upload`, `icon-picker`, `hidden-field`, and `phone-input` are available but don't have YAML documentation yet.

### Visual Components

- [`map`](../components/visual/map.yaml) - Map display with markers
- [`divider`](../components/visual/divider.yaml) - Divider/separator line

### Progress Components

- [`linear-progress`](../components/progress/linear-progress.yaml) - Linear progress bar
- [`circular-progress`](../components/progress/circular-progress.yaml) - Circular progress indicator

### Chart Components

- [`bar-chart`](../components/chart/bar-chart.yaml) - Bar chart (use type: `bar`)
- [`pie-chart`](../components/chart/pie-chart.yaml) - Pie chart (use type: `pie`)

### Utility Components

- [`login-form`](../components/utility/login-form.yaml) - Login form
- [`vertical-menu`](../components/utility/vertical-menu.yaml) - Vertical navigation menu
- [`calendar`](../components/utility/calendar.yaml) - Calendar component
- [`prompt`](../components/utility/prompt.yaml) - Prompt/input dialog
- [`quantity`](../components/utility/quantity.yaml) - Quantity selector
- [`pricing`](../components/utility/pricing.yaml) - Pricing table
- [`newsletter`](../components/utility/newsletter.yaml) - Newsletter signup
- [`alert`](../components/utility/alert.yaml) - Alert/notification component

### Interactive Components

- [`comment`](../components/interactive/comment.yaml) - Comment system
- [`rating`](../components/interactive/rating.yaml) - Rating display/input

**📖 For detailed property specifications, format requirements, and examples, see the [Component Specifications](../components/) directory.**

---

## Common Properties

Most components share common styling and layout properties such as `width`, `alignment`, `margin`, `padding`, `typography`, `color`, `backgroundColor`, and `cornerRadius`.

**📖 For complete format documentation and examples of all common properties, see the [Format Documentation](../format/index.md) directory:**
- [Sizing Format](../format/styles/sizing.md) - Width, height, and sizing properties
- [Alignment Format](../format/styles/alignments.md) - Horizontal and vertical alignment
- [Spacing Format](../format/styles/spacing.md) - Margin and padding
- [Typography Format](../format/styles/typography.md) - Text typography variants
- [Colors Format](../format/styles/colors.md) - Color tokens and formats
- [Corner Radius Format](../format/styles/corner-radius.md) - Shape and corner radius
- And more...

---

## Container Components

Container components can have nested children:

### Section Component

```json
{
  "type": "section",
  "orientation": "v",
  "layout": "cols:100",
  "padding": "p:40px",
  "gap": "gap:24px",
  "background": "solid:primary-95",
  "align": "h:center",
  "children": [
    {
      "type": "text",
      "content": ["text:Child component"]
    }
  ]
}
```

**See also:** [Section Component Specification](../components/container/section.yaml)

### Form Component

```json
{
  "type": "form",
  "tableId": "table-id",
  "compTitle": ["text:Contact Form"],
  "width": "w:100% de:w:600px",
  "children": [
    {
      "type": "text-field",
      "label": ["text:Name"],
      "columnId": "name-column-id"
    },
    {
      "type": "button",
      "label": ["text:Submit"]
    }
  ]
}
```

**See also:** [Form Component Specification](../components/container/form.yaml)

---

## Component-Specific Properties

Each component type has its own specific properties with detailed format requirements. All components have comprehensive YAML specifications that document:

- **All available properties** - Complete list of properties for each component
- **Property types** - Data types (string, array, boolean, object, etc.)
- **Format strings** - Exact format syntax for each property
- **Format documentation links** - References to format documentation
- **Default values** - Default values where applicable

### Quick Reference

- **Text Components:** `content` (array), `typography`, `color`, `align` - See [Text](../components/text/text.yaml) and [Rich Text](../components/text/rich-text.yaml)
- **Button Components:** `label` (array), `backgroundColor`, `size`, `shape`, `icon` - See [Button](../components/button/button.yaml), [FAB](../components/button/fab.yaml), [Icon](../components/button/icon.yaml)
- **Media Components:** `src`, `imageTitle`/`videoTitle` (arrays), `width`, `aspectRatio` - See [Image](../components/media/image.yaml), [Video](../components/media/video.yaml), [Audio](../components/media/audio.yaml)
- **List Components:** `dataSource`, `titleColumn`, `mediaColumn`, `columns`, `rows` - See [List](../components/list/list.yaml), [Card](../components/list/card.yaml), [Gallery](../components/list/gallery.yaml)
- **Form Components:** `tableId`, `compTitle` (array), `columnId`, `label` (array) - See [Form](../components/container/form.yaml), [TextField](../components/form/text-field.yaml)

**📖 For complete property lists and format specifications, see the [Component Specifications](../components/) directory.**

**See also:** [Component Parser Workflow](../component-parser-workflow.md) for implementation details

---

## Special Components

Some components are **special** because they automatically generate child component structures that don't directly map to the input JSON. These components require custom parsing logic to create their internal structure.

### What Makes a Component Special?

Special components:
- **Auto-generate child structures** - They create child components automatically based on input data
- **Use different input format** - The input structure differs from the output structure
- **Require custom parsing** - They use special parser functions instead of the standard component parser

### Special Component Types

#### Tabs Component

The `tabs` component automatically generates `tab-item` children from a `tabs` array in the input.

**Input Structure:**
```json
{
  "type": "tabs",
  "tabs": [
    {
      "title": "Tab 1",
      "icon": "icon:home",
      "children": [
        {
          "type": "text",
          "content": ["text:Content for Tab 1"]
        }
      ]
    },
    {
      "title": "Tab 2",
      "icon": "icon:settings",
      "children": [
        {
          "type": "text",
          "content": ["text:Content for Tab 2"]
        }
      ]
    }
  ],
  "orientation": "horizontal",
  "variant": "default",
  "width": "w:100%"
}
```

**How it works:**
- The `tabs` array defines each tab
- Each tab has a `title`, optional `icon`, and `children` array
- The parser automatically creates `tab-item` components for each tab
- Each `tab-item` contains the parsed children from that tab's `children` array

**See also:** [Tabs Component Specification](../components/container/tabs.yaml)

#### Form Component

The `form` component automatically generates form field children and a submit button from the `children` array and `submitButton` configuration.

**Input Structure:**
```json
{
  "type": "form",
  "tableId": "table-id",
  "compTitle": ["text:Contact Form"],
  "submitButton": {
    "label": ["text:Submit"],
    "backgroundColor": "solid:primary-40",
    "size": "lg"
  },
  "children": [
    {
      "type": "text-field",
      "label": ["text:Name"],
      "columnId": "name-column-id"
    },
    {
      "type": "text-field",
      "label": ["text:Email"],
      "columnId": "email-column-id"
    }
  ]
}
```

**How it works:**
- The `children` array contains form field components (text-field, checkbox, etc.)
- Each field must have a `columnId` to map to table columns
- The `submitButton` configuration automatically creates a submit button
- Set `submitButton` to `null` to disable the submit button
- The parser creates the form structure with all fields and the submit button

**See also:** [Form Component Specification](../components/container/form.yaml)

### Differences from Regular Components

| Aspect | Regular Components | Special Components |
|--------|-------------------|-------------------|
| **Child Structure** | Direct mapping from `children` array | Auto-generated from input data |
| **Input Format** | Matches output structure | Different from output structure |
| **Parser** | Standard component parser | Special parser function |
| **Examples** | `section`, `text`, `button`, `image` | `tabs`, `form` |

### Using Special Components

When using special components in your JSON:

1. **Follow the special input format** - Use the structure documented in the component specification
2. **Don't manually create child structures** - Let the parser handle it automatically
3. **Provide required data** - Special components need specific data (e.g., `tabs` array for tabs, `tableId` for forms)

### Implementation Notes

Special components are handled differently in the parser system:
- They use `SPECIAL_COMPONENT_PARSERS` registry instead of `COMPONENT_PARSER_REGISTRY`
- They return full `IBody` structures instead of just settings
- They handle recursive parsing of nested children automatically

**See also:** [Component Parser Workflow](../component-parser-workflow.md) for implementation details

---

## Complete Example

```json
{
  "type": "section",
  "orientation": "v",
  "padding": "p:40px",
  "gap": "gap:24px",
  "background": "solid:primary-95",
  "children": [
    {
      "type": "text",
      "content": ["text:Welcome to our page"],
      "typography": "headline-large",
      "color": "solid:primary-20",
      "align": "t:center",
      "margin": "mb:16px"
    },
    {
      "type": "button",
      "label": ["text:Get Started"],
      "backgroundColor": "solid:primary-40",
      "size": "lg",
      "shape": "medium",
      "align": "h:center"
    }
  ]
}
```

**Key points:**
- `content` and `label` are arrays using text format (e.g., `["text:Welcome"]`)
- `background` uses color tokens (e.g., `primary-95` for common backgrounds, `primary-40` for accents)
- `align` property name (not `alignment` for button)
- See [Component Specifications](../components/) for complete property lists

---

## Related Documentation

- **[Component Specifications](../components/)** - Detailed YAML specifications for all components with complete property lists and format requirements
- [Component Parser Workflow](../component-parser-workflow.md) - How to create component parsers
- [Format Documentation](../format/index.md) - Component settings format (spacing, colors, typography, etc.)
- [Page Format](page.md) - How to use components in pages
- [Overlay Format](overlay.md) - How to use components in overlays
- [Globals Format](globals.md) - How to use components in global settings (future)
