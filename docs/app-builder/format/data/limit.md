# Limit Documentation

## Overview

The limit format controls how many rows are displayed in data components like tables and lists. It supports multiple formats from simple to advanced, allowing you to compress JSON size while maintaining flexibility.

---

## Limit Structure

**Syntax:**
```typescript
limit: number | string | {
  enabled: boolean
  limit: number  // Max limit
  value: number  // Actual limit value
}
```

The limit can be specified in three ways:

1. **Simple number** - Just the value (enabled = true)
2. **Compact string** - Compressed key-value format (recommended)
3. **Object format** - Full object with all properties (for advanced use cases)

---

## Simple Number Format

**Syntax:** `<number>`

When a number is provided, it sets the `value` to that number, `enabled` to `true`, and `limit` (max) to `100`.

**Example:**
```typescript
limit: 10
```

This is equivalent to:
```typescript
limit: {
  enabled: true,
  limit: 100,
  value: 10
}
```

---

## Compact String Format

**Syntax:** `"limit:<value> [en:<true|false>] [max:<max-limit>]"`

**Format:**
- `limit:` - Value (required) - The actual number of rows to display
- `en:` - Enabled flag (optional, defaults to `false`) - Whether the limit is active
- `max:` - Maximum limit (optional, defaults to `100`) - The maximum allowed limit

**Examples:**
```typescript
// Just value (enabled defaults to false)
limit: "limit:10"

// With enabled flag
limit: "limit:10 en:true"

// With all properties
limit: "limit:10 en:false max:100"

// Enabled with custom max
limit: "limit:20 en:true max:200"

// Disabled limit
limit: "limit:10 en:false"

// Large limit with custom max
limit: "limit:50 en:true max:500"
```

---

## Object Format (Advanced)

**Syntax:**
```typescript
{
  enabled: boolean
  limit: number  // Max limit
  value: number  // Actual limit value
}
```

**Properties:**

| Property | Type | Required | Description |
|----------|------|----------|-------------|
| `enabled` | `boolean` | No | Whether the limit is active (defaults to `false`) |
| `limit` | `number` | No | Maximum allowed limit (defaults to `100`) |
| `value` | `number` | No | Actual number of rows to display (defaults to `10`) |

**Example:**
```typescript
limit: {
  enabled: false,
  limit: 100,
  value: 10
}
```

---

## Complete Examples

### Simple Number
```typescript
{
  type: "data-table",
  limit: 10
}
```

### Compact Format
```typescript
{
  type: "data-table",
  limit: "limit:10 en:false max:100"
}
```

### Object Format
```typescript
{
  type: "data-table",
  limit: {
    enabled: false,
    limit: 100,
    value: 10
  }
}
```

### Different Scenarios
```typescript
// Enabled limit with 20 rows
limit: "limit:20 en:true"

// Disabled limit (shows all rows)
limit: "limit:10 en:false"

// Large dataset with custom max
limit: "limit:100 en:true max:1000"

// Simple enabled limit
limit: 25  // Equivalent to "limit:25 en:true max:100"
```

---

## Size Comparison

**Object Format** (~45 bytes):
```json
{
  "enabled": false,
  "limit": 100,
  "value": 10
}
```

**Compact Format** (~28 bytes):
```json
"limit:10 en:false max:100"
```

**Savings:** ~38% reduction in JSON size

---

## Limit Reference

| Format | Syntax | Size | Use Case |
|--------|--------|------|----------|
| Simple Number | `<number>` | Smallest | Quick setup, enabled limit |
| Compact String | `"limit:<value> [en:<flag>] [max:<max>]"` | Medium | Recommended for most cases |
| Object | `{ enabled, limit, value }` | Largest | Complex requirements |

### Property Reference

| Property | Description | Default |
|----------|-------------|---------|
| `value` | Number of rows to display | `10` |
| `enabled` | Whether limit is active | `false` |
| `limit` (max) | Maximum allowed limit | `100` |

---

## Notes

- When `enabled` is `false`, the limit is not applied and all rows are shown
- When `enabled` is `true`, only `value` number of rows are displayed
- The `limit` (max) property sets the maximum allowed limit value
- Simple number format automatically sets `enabled` to `true`
- Compact format is recommended for optimal JSON size while maintaining readability
- All properties are optional in object format and will use defaults if omitted

