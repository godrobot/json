# Page Format Documentation

## Overview

The Page format defines the simplified input structure for creating pages in the Makyo App Builder. Pages are the main screens of your application and can contain components, navigation bars, and SEO settings.

---

## Simplified Input Structure

```typescript
interface AiPageInput {
  title: string                    // Page title (required)
  icon?: string                    // Material icon name (optional)
  backgroundColor?: string          // Background color from brand kit (optional)
  components: AiComponentInput[]    // Array of component inputs (required)
  topBar?: {                        // Top bar configuration (optional)
    type?: 'default' | 'minimal' | 'none'
    showTitle?: boolean
  }
  bottomBar?: {                     // Bottom bar configuration (optional)
    type?: 'default' | 'none'
  }
  seo?: {                           // SEO settings (optional)
    title?: string
    description?: string
    keywords?: string
  }
}
```

---

## Properties

### `title` (required)
The page title displayed in navigation and browser tabs.

**Type:** `string`

**Example:**
```json
{
  "title": "Product Launch"
}
```

---

### `icon` (optional)
Material icon name for the page. Used in navigation menus and page headers.

**Type:** `string`

**Default:** `"draft"`

**Example:**
```json
{
  "icon": "rocket_launch"
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
  "backgroundColor": "primary-98"
}
```

**See also:** [Colors Format](../format/styles/colors.md)

---

### `components` (required)
Array of component inputs that make up the page content.

**Type:** `AiComponentInput[]`

**Example:**
```json
{
  "components": [
    {
      "type": "section",
      "orientation": "v",
      "children": [
        {
          "type": "text",
          "content": "Welcome to our page"
        }
      ]
    }
  ]
}
```

**See also:** [Component Parser Workflow](../component-parser-workflow.md)

---

### `topBar` (optional)
Configuration for the top navigation bar.

**Properties:**
- `type`: Bar type - `'default'` | `'minimal'` | `'none'`
- `showTitle`: Whether to show the page title in the bar (default: `true`)

**Example:**
```json
{
  "topBar": {
    "type": "default",
    "showTitle": true
  }
}
```

---

### `bottomBar` (optional)
Configuration for the bottom navigation bar.

**Properties:**
- `type`: Bar type - `'default'` | `'none'`

**Example:**
```json
{
  "bottomBar": {
    "type": "default"
  }
}
```

---

### `seo` (optional)
Search engine optimization settings for the page.

**Properties:**
- `title`: Meta title for search engines
- `description`: Meta description for search results
- `keywords`: Meta keywords (comma-separated)

**Example:**
```json
{
  "seo": {
    "title": "Product Launch - Makyo",
    "description": "Learn about our latest product launch",
    "keywords": "product, launch, makyo"
  }
}
```

---

## Complete Example

```json
{
  "title": "Product Launch",
  "icon": "rocket_launch",
  "backgroundColor": "primary-98",
  "topBar": {
    "type": "default",
    "showTitle": true
  },
  "bottomBar": {
    "type": "default"
  },
  "seo": {
    "title": "Product Launch - Makyo",
    "description": "Learn about our latest product launch",
    "keywords": "product, launch, makyo"
  },
  "components": [
    {
      "type": "section",
      "orientation": "v",
      "children": [
        {
          "type": "text",
          "content": "🚀 Launch Your Ideas",
          "typography": "display-small"
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
- [Spacing Format](../format/styles/spacing.md)
- [Typography Format](../format/styles/typography.md)

