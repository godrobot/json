# App Builder Documentation

Welcome to the Makyo App Builder documentation. This documentation provides comprehensive guides for creating applications using the simplified AI-friendly input formats.

## Overview

The Makyo App Builder allows you to create applications using simplified JSON structures that are parsed into full App Builder component trees. This system is designed to be AI-friendly, making it easy for AI systems to generate complete application structures.

---

## Quick Start

1. **Understand Components** - Learn about the building blocks: [Component Format](builders/component.md)
2. **Learn Formats** - Understand property formats: [Format Documentation](format/index.md)
3. **Create Pages** - Build your first page: [Page Format](builders/page.md)
4. **Add Components** - Explore component specifications: [Component Specifications](components/)

---

## Documentation Structure

### 📦 [Builders](builders/index.md)

Documentation for App Builder entities - the high-level structures that make up your application:

- **[Components](builders/component.md)** - Component building blocks (sections, text, buttons, forms, etc.)
- **[Pages](builders/page.md)** - Main application pages with navigation and SEO
- **[Overlays](builders/overlay.md)** - Modal overlays and sheets
- **[Dialogs](builders/dialog.md)** - Alert dialogs and confirmations
- **[Menus](builders/menu.md)** - Contextual menus and navigation
- **[Globals](builders/globals.md)** - Global components (future implementation)

### 🎨 [Format Documentation](format/index.md)

Complete reference for all format strings used in component properties:

#### Data Formats

- **[Text Data](format/data/text.md)** - Text content with variable references
- **[Select Data](format/data/select.md)** - Icon, column, and profile selections
- **[Datasource](format/data/datasource.md)** - Table data sources
- **[Limit](format/data/limit.md)** - Pagination and limits

#### Style Formats

- **[Colors](format/styles/colors.md)** - Color tokens and formats (solid, gradient, adaptive)
- **[Typography](format/styles/typography.md)** - Text typography variants
- **[Spacing](format/styles/spacing.md)** - Margin and padding
- **[Sizing](format/styles/sizing.md)** - Width and height
- **[Alignments](format/styles/alignments.md)** - Horizontal and vertical alignment
- **[Corner Radius](format/styles/corner-radius.md)** - Shape and border radius
- **[Breakpoints](format/styles/breakpoints.md)** - Responsive breakpoint formats
- **[Layout](format/styles/layout.md)** - Column layouts
- **[Orientation](format/styles/orientation.md)** - Horizontal/vertical orientation
- **[Aspect Ratio](format/styles/aspect-ratio.md)** - Image and media aspect ratios
- **[Borders](format/styles/borders.md)** - Border styles
- **[Shadows](format/styles/shadows.md)** - Shadow effects
- **[Effects](format/styles/effects.md)** - Visual effects
- **[Patterns](format/styles/patterns.md)** - Background patterns
- **[Section Variant](format/styles/section-variant.md)** - Section variants

### 🧩 [Component Specifications](components/)

Detailed YAML specifications for all available components, organized by group:

#### Container Components

- [Section](components/container/section.yaml) - Layout container
- [Tabs](components/container/tabs.yaml) - Tabbed interface
- [Form](components/container/form.yaml) - Form container

#### Text Components

- [Text](components/text/text.yaml) - Simple text display
- [Rich Text](components/text/rich-text.yaml) - Markdown/HTML content

#### Button Components

- [Button](components/button/button.yaml) - Standard button
- [FAB](components/button/fab.yaml) - Floating action button
- [Icon](components/button/icon.yaml) - Icon button

#### Media Components

- [Image](components/media/image.yaml) - Image display
- [Video](components/media/video.yaml) - Video player
- [Audio](components/media/audio.yaml) - Audio player

#### List Components

- [List](components/list/list.yaml) - Simple list
- [Card](components/list/card.yaml) - Card-based list
- [Gallery](components/list/gallery.yaml) - Image gallery
- [Accordion](components/list/accordion.yaml) - Expandable accordion
- [Timeline](components/list/timeline.yaml) - Timeline display
- [Shopping Cart](components/list/shopping-cart.yaml) - Shopping cart

#### Table Components

- [Data Table](components/table/data-table.yaml) - Full-featured table
- [Single Row](components/table/single-row.yaml) - Single row data list

#### Form Field Components

- [Text Field](components/form/text-field.yaml) - Text input
- [Checkbox](components/form/checkbox.yaml) - Checkbox input
- [Switch](components/form/switch.yaml) - Toggle switch
- [Selection](components/form/selection.yaml) - Dropdown/picker
- [Slider](components/form/slider.yaml) - Range slider

#### Visual Components

- [Map](components/visual/map.yaml) - Map with markers
- [Divider](components/visual/divider.yaml) - Divider/separator

#### Progress Components

- [Linear Progress](components/progress/linear-progress.yaml) - Progress bar
- [Circular Progress](components/progress/circular-progress.yaml) - Progress indicator

#### Chart Components

- [Bar Chart](components/chart/bar-chart.yaml) - Bar chart
- [Pie Chart](components/chart/pie-chart.yaml) - Pie chart

#### Utility Components

- [Alert](components/utility/alert.yaml) - Alert/notification
- [Calendar](components/utility/calendar.yaml) - Calendar component
- [Login Form](components/utility/login-form.yaml) - Login form
- [Newsletter](components/utility/newsletter.yaml) - Newsletter signup
- [Pricing](components/utility/pricing.yaml) - Pricing table
- [Prompt](components/utility/prompt.yaml) - Input dialog
- [Quantity](components/utility/quantity.yaml) - Quantity selector
- [Vertical Menu](components/utility/vertical-menu.yaml) - Navigation menu

#### Interactive Components

- [Comment](components/interactive/comment.yaml) - Comment system
- [Rating](components/interactive/rating.yaml) - Rating display/input

---

## Key Concepts

### Component System

Components are the building blocks of your application. Each component:

- Has a specific `type` (e.g., `"button"`, `"text"`, `"section"`)
- Can have properties specific to its type
- Can contain nested `children` (for container components)
- Uses format strings for styling (colors, spacing, typography, etc.)

**See:** [Component Format](builders/component.md)

### Format Strings

Properties use format strings to define values:

- **Colors:** `"solid:primary-40"`, `"gradient:primary-40|primary-80:to-right"`, `"adaptive"`
- **Spacing:** `"p:16px"`, `"m:2rem ta:m:3rem"`
- **Typography:** `"headline-large"`, `"body-medium ta:body-large"`
- **Sizing:** `"w:100%"`, `"w:300px de:w:600px"`

**See:** [Format Documentation](format/index.md)

### Color Token System

The system uses a token-based color approach:

- **Palettes:** `primary`, `secondary`, `tertiary`, `neutral`
- **Tones:** `0`, `5`, `10`, `20`, `30`, `40`, `50`, `60`, `70`, `80`, `90`, `95`, `100`
- **Format:** `<palette>-<tone>` (e.g., `primary-40`, `neutral-95`)
- **Important:** Tones are inverted between light and dark themes for proper contrast

**See:** [Colors Format](format/styles/colors.md)

### Special Components

Some components are "special" because they auto-generate child structures:

- **Tabs** - Automatically creates `tab-item` children from a `tabs` array
- **Form** - Automatically creates form fields and submit button from `children` array

**See:** [Component Format - Special Components](builders/component.md#special-components)

---

## Workflow Guides

### For AI Systems

1. **Start with a Page** - Create the page structure: [Page Format](builders/page.md)
2. **Add Components** - Use component specifications: [Component Specifications](components/)
3. **Apply Formats** - Use format strings for properties: [Format Documentation](format/index.md)
4. **Use Color Tokens** - Reference color tokens: [Colors Format](format/styles/colors.md)

### For Developers

1. **Understand Parsers** - Learn how parsers work: [Component Parser Workflow](component-parser-workflow.md)
2. **Create Components** - Follow the workflow: [Component Parser Workflow](component-parser-workflow.md)
3. **Document Components** - Add YAML specs: [Component Documentation Workflow](components/component-documentation-workflow.md)

---

## Related Documentation

- [Component Parser Workflow](component-parser-workflow.md) - How component parsers work internally
- [Parser System Plan](parser-system-plan.md) - Implementation plan for the parser system
- [Component Documentation Workflow](components/component-documentation-workflow.md) - How to document components

---

## Examples

### Simple Page with Components

```json
{
  "title": "Welcome Page",
  "components": [
    {
      "type": "section",
      "padding": "p:40px",
      "background": ["color:solid:primary-95"],
      "children": [
        {
          "type": "text",
          "content": ["text:Welcome to our app"],
          "typography": "headline-large",
          "color": "solid:primary-20"
        },
        {
          "type": "button",
          "label": ["text:Get Started"],
          "backgroundColor": "solid:primary-40"
        }
      ]
    }
  ]
}
```

**See:** [Component Format](builders/component.md) for more examples

---

## Getting Help

- Check component specifications: [Component Specifications](components/)
- Review format documentation: [Format Documentation](format/index.md)
- Understand parser workflow: [Component Parser Workflow](component-parser-workflow.md)
