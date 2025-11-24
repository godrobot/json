# Menu Format Documentation

## Overview

The Menu format defines the simplified input structure for creating menus in the Makyo App Builder. Menus are used for contextual actions, navigation, and user interactions. They can contain multiple menu items, each with an icon, label, and optional actions.

---

## Simplified Input Structure

```typescript
interface AiMenuInput {
  title: string                    // Menu title (required)
  items: AiMenuItemInput[]           // Array of menu items (required)
  visibility?: {                   // Visibility conditions (optional)
    conditions?: any[]
    isAny?: boolean
  }
}

interface AiMenuItemInput {
  title: string                    // Menu item label (required)
  icon?: string                     // Material icon name (optional)
  badgeSize?: 's' | 'm' | 'l' | '' // Badge size (optional)
  badgeMetadata?: Record<string, any> // Badge data (optional)
  actions?: any[]                   // Actions array (optional, deferred to action parser)
  visibility?: {                   // Visibility conditions (optional)
    conditions?: any[]
    isAny?: boolean
  }
}
```

---

## Properties

### `title` (required)
The menu title displayed in the menu header or used for identification.

**Type:** `string`

**Example:**
```json
{
  "title": "Article Query Menu"
}
```

---

### `items` (required)
Array of menu items that make up the menu.

**Type:** `AiMenuItemInput[]`

**Example:**
```json
{
  "items": [
    {
      "title": "Update",
      "icon": "edit_square"
    },
    {
      "title": "Delete",
      "icon": "delete"
    }
  ]
}
```

---

### `visibility` (optional)
Controls when the menu is visible based on conditions.

**Properties:**
- `conditions`: Array of visibility conditions
- `isAny`: If `true`, menu is visible if ANY condition is true; if `false`, ALL conditions must be true

**Default:** Empty object `{}`

**Example:**
```json
{
  "visibility": {
    "conditions": [],
    "isAny": true
  }
}
```

---

## Menu Item Properties

### `title` (required)
The menu item label displayed to the user.

**Type:** `string`

**Example:**
```json
{
  "title": "Update"
}
```

---

### `icon` (optional)
Material icon name displayed next to the menu item label.

**Type:** `string`

**Default:** Empty string (no icon)

**Example:**
```json
{
  "icon": "edit_square"
}
```

**See also:** [Material Icons](https://fonts.google.com/icons)

---

### `badgeSize` (optional)
Size of the badge displayed on the menu item.

**Type:** `'s'` | `'m'` | `'l'` | ''`

**Default:** `''` (no badge)

**Example:**
```json
{
  "badgeSize": "s"
}
```

---

### `badgeMetadata` (optional)
Metadata for the badge (e.g., badge count, color, etc.).

**Type:** `Record<string, any>`

**Default:** `{}`

**Example:**
```json
{
  "badgeMetadata": {
    "count": 5,
    "color": "primary-50"
  }
}
```

---

### `actions` (optional)
Array of actions to execute when the menu item is clicked.

**Type:** `any[]`

**Note:** Action parsing is deferred to the action parser system (future implementation).

**Default:** Empty array `[]`

**Example:**
```json
{
  "actions": [
    {
      "type": "nav_go-to-screen",
      "settings": {
        "screen": "page-id"
      }
    }
  ]
}
```

**See also:** Action Parser (future implementation)

---

### `visibility` (optional)
Controls when the menu item is visible based on conditions.

**Properties:**
- `conditions`: Array of visibility conditions
- `isAny`: If `true`, item is visible if ANY condition is true; if `false`, ALL conditions must be true

**Default:** Empty object `{}`

**Example:**
```json
{
  "visibility": {
    "conditions": [],
    "isAny": true
  }
}
```

---

## Complete Example

```json
{
  "title": "Article Query Menu",
  "items": [
    {
      "title": "Update",
      "icon": "edit_square",
      "badgeSize": "s"
    },
    {
      "title": "Delete",
      "icon": "delete",
      "badgeSize": "s"
    },
    {
      "title": "Duplicate",
      "icon": "content_copy",
      "badgeSize": "s"
    },
    {
      "title": "Share",
      "icon": "share",
      "badgeSize": ""
    }
  ],
  "visibility": {
    "conditions": [],
    "isAny": true
  }
}
```

---

## Common Use Cases

### Contextual Menu
A menu that appears when right-clicking or long-pressing an item:

```json
{
  "title": "Item Actions",
  "items": [
    {
      "title": "Edit",
      "icon": "edit"
    },
    {
      "title": "Delete",
      "icon": "delete"
    }
  ]
}
```

### Navigation Menu
A menu used for navigation between pages:

```json
{
  "title": "Main Navigation",
  "items": [
    {
      "title": "Home",
      "icon": "home"
    },
    {
      "title": "Profile",
      "icon": "person"
    },
    {
      "title": "Settings",
      "icon": "settings"
    }
  ]
}
```

### Menu with Badges
A menu with notification badges:

```json
{
  "title": "Notifications",
  "items": [
    {
      "title": "Messages",
      "icon": "mail",
      "badgeSize": "s",
      "badgeMetadata": {
        "count": 5
      }
    }
  ]
}
```

---

## Related Documentation

- [Component Parser Workflow](../component-parser-workflow.md)
- Action Parser (future implementation)

