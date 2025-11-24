# Data Source Documentation

## Overview

The data source format defines how to specify table data sources with column configurations for components like data tables. It supports multiple formats from simple to advanced, allowing you to compress JSON size while maintaining flexibility.

---

## Data Source Structure

**Syntax:**
```typescript
dataSource: string | {
  table: string
  columns?: AiDataTableColumn[]
  isDetailPageTable?: boolean
}
```

The data source can be specified in three ways:

1. **Simple string** - Just the table ID (uses all columns from table)
2. **Simplified object** - Table ID with optional column definitions
3. **Full object** - Complete complex object (for advanced use cases)

---

## Simple Format

**Syntax:** `"<table-id>"`

When a string is provided, it's treated as the table ID and all columns from the table are used.

**Example:**
```typescript
dataSource: "d5b28b3e-40a3-43a6-8c67-3a33088810e5"
```

---

## Simplified Format

**Syntax:**
```typescript
{
  table: string
  columns?: AiDataTableColumn[]
  isDetailPageTable?: boolean
}
```

### Properties

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `table` | `string` | Yes | The table ID to use as data source |
| `columns` | `AiDataTableColumn[]` | No | Array of column definitions (if omitted, uses all columns) |
| `isDetailPageTable` | `boolean` | No | Whether this is a detail page table (defaults to `false`) |

**Example:**
```typescript
dataSource: {
  table: "d5b28b3e-40a3-43a6-8c67-3a33088810e5",
  columns: [
    "Cf35zy",
    "col:A9G3s4 lbl:Short Text",
    "col:mdFY57 lbl:Date 1 ic:calendar"
  ],
  isDetailPageTable: false
}
```

---

## Column Definitions

Columns can be specified in three formats:

### 1. Simple String (Column ID Only)

**Syntax:** `"<column-id>"`

**Example:**
```typescript
columns: ["Cf35zy", "A9G3s4"]
```

This format uses the column ID as both the identifier and label, with default icon (`star`) and visibility (all breakpoints visible).

---

### 2. Compact String Format

**Syntax:** `"col:<id> [lbl:<label>] [ic:<icon>] [us:<true|false>] [vs:<visibility>]"`

**Format:**
- `col:` - Column ID (required)
- `lbl:` - Display label (optional, supports spaces)
- `ic:` - Icon name (optional, defaults to `star`)
- `us:` - User specific flag (optional, `true` or `false`, defaults to `false`)
- `vs:` - Visibility (optional):
  - `vs:true` or `vs:false` - All breakpoints
  - `vs:ph:true ta:false de:true` - Responsive visibility

**Breakpoint Abbreviations:**

| Breakpoint | Abbreviation | Description |
|------------|--------------|-------------|
| Phone | `ph:` | Mobile portrait |
| Phone Landscape | `pl:` | Mobile landscape |
| Tablet | `ta:` | Tablet portrait |
| Tablet Landscape | `tl:` | Tablet landscape |
| Desktop | `de:` | Desktop screens (also applies to TV) |
| TV | `tv:` | Large displays |

**Examples:**
```typescript
// Column ID only
columns: ["col:Cf35zy"]

// With label
columns: ["col:A9G3s4 lbl:Short Text"]

// With label and icon
columns: ["col:mdFY57 lbl:Date 1 ic:calendar"]

// With all properties
columns: ["col:8qaX4Q lbl:Email ic:mail us:false vs:true"]

// With responsive visibility
columns: ["col:rp33eb lbl:Status ic:check vs:ph:true ta:true de:false"]

// Multiple breakpoint visibility
columns: ["col:abPcNc lbl:URL ic:link vs:ph:false ta:true de:true"]
```

**Visibility Examples:**
```typescript
// Visible on all breakpoints
"col:Cf35zy vs:true"

// Hidden on all breakpoints
"col:Cf35zy vs:false"

// Visible on phone, hidden on tablet and desktop
"col:Cf35zy vs:ph:true ta:false de:false"

// Visible on phone and tablet, hidden on desktop
"col:Cf35zy vs:ph:true ta:true de:false"

// Complex responsive visibility
"col:Cf35zy vs:ph:true pl:true ta:false tl:false de:true tv:true"
```

---

### 3. Object Format (Advanced)

**Syntax:**
```typescript
{
  columnId: string
  label?: string
  icon?: string
  visible?: boolean | {
    phone?: boolean
    tablet?: boolean
    desktop?: boolean
  }
}
```

**Example:**
```typescript
columns: [
  {
    columnId: "Cf35zy",
    label: "ID",
    icon: "star",
    visible: true
  },
  {
    columnId: "A9G3s4",
    label: "Short Text",
    icon: "text",
    visible: {
      phone: true,
      tablet: true,
      desktop: false
    }
  }
]
```

---

## Complete Examples

### Simple Data Source
```typescript
{
  type: "data-table",
  dataSource: "d5b28b3e-40a3-43a6-8c67-3a33088810e5"
}
```

### Simplified with Columns
```typescript
{
  type: "data-table",
  dataSource: {
    table: "d5b28b3e-40a3-43a6-8c67-3a33088810e5",
    columns: [
      "Cf35zy",
      "col:A9G3s4 lbl:Short Text",
      "col:mdFY57 lbl:Date 1",
      "col:rp33eb lbl:Boolean",
      "col:8qaX4Q lbl:Email ic:mail"
    ]
  }
}
```

### Mixed Column Formats
```typescript
{
  type: "data-table",
  dataSource: {
    table: "d5b28b3e-40a3-43a6-8c67-3a33088810e5",
    columns: [
      "Cf35zy",  // Simple string
      "col:A9G3s4 lbl:Short Text",  // Compact format
      {
        columnId: "mdFY57",
        label: "Date 1",
        icon: "calendar",
        visible: { phone: true, desktop: false }
      }
    ]
  }
}
```

### With Responsive Visibility
```typescript
{
  type: "data-table",
  dataSource: {
    table: "d5b28b3e-40a3-43a6-8c67-3a33088810e5",
    columns: [
      "col:Cf35zy lbl:ID vs:true",
      "col:A9G3s4 lbl:Title vs:ph:true ta:true de:true",
      "col:mdFY57 lbl:Date vs:ph:false ta:true de:true",
      "col:rp33eb lbl:Status vs:ph:true ta:false de:false"
    ]
  }
}
```

---

## Size Comparison

**Object Format** (~60 bytes per column):
```json
{
  "columnId": "A9G3s4",
  "label": "Short Text",
  "icon": "star"
}
```

**Compact Format** (~35 bytes per column):
```json
"col:A9G3s4 lbl:Short Text ic:star"
```

**Savings:** ~42% reduction in JSON size

---

## Data Source Reference

| Format | Syntax | Use Case |
|--------|--------|----------|
| Simple String | `"<table-id>"` | Use all columns from table |
| Simplified Object | `{ table, columns?, isDetailPageTable? }` | Recommended for most cases |
| Full Object | Complex object structure | Advanced scenarios |

### Column Format Reference

| Format | Syntax | Size | Use Case |
|--------|--------|------|----------|
| Simple String | `"<column-id>"` | Smallest | Quick setup, defaults are fine |
| Compact String | `"col:<id> [lbl:<label>] [ic:<icon>] [us:<flag>] [vs:<visibility>]"` | Medium | Recommended for most cases |
| Object | `{ columnId, label?, icon?, visible? }` | Largest | Complex visibility requirements |

### Visibility Reference

| Format | Syntax | Description |
|--------|--------|-------------|
| All Breakpoints | `vs:true` or `vs:false` | Same visibility for all devices |
| Responsive | `vs:ph:<bool> ta:<bool> de:<bool>` | Different visibility per breakpoint |

### Breakpoint Abbreviations Reference

| Breakpoint | Abbreviation | Full Name |
|------------|--------------|-----------|
| `ph:` | Phone | Mobile portrait |
| `pl:` | Phone Landscape | Mobile landscape |
| `ta:` | Tablet | Tablet portrait |
| `tl:` | Tablet Landscape | Tablet landscape |
| `de:` | Desktop | Desktop screens (also applies to TV) |
| `tv:` | TV | Large displays |

## Notes

- Column IDs are required and must match columns in the specified table
- Labels support spaces and special characters
- Icons default to `"star"` if not specified
- Visibility defaults to `true` (visible) on all breakpoints if not specified
- User specific flag defaults to `false` if not specified
- When `columns` is omitted, all columns from the table are used
- Compact format is recommended for optimal JSON size while maintaining readability
- For limit format details, see [Limit Documentation](limit.md)

