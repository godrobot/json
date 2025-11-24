# Text Documentation

## Overview

The text component allows combining multiple data sources into a single text output. It supports mixing static text with dynamic values from various select types.

---

## Text Syntax

**Syntax:** `[<select-type>, <select-type>, ...]`

Text is composed of one or more [data select](select.md) types combined as an array.

**Example:**
```typescript
text: ["text:Hello World"]
text: ["text:The best product is ", "sc:products:name:12"]
text: ["profile:username", "text: ordered ", "cr:quantity", "text: items"]
```

---

## Examples

```typescript
// Static text only
text: ["text:Welcome to our app"]

// Text with profile data
text: ["text:Hello, ", "profile:username"]

// Text with table data
text: ["text:The best product is ", "sc:products:name:12"]

// Text with current row data
text: ["cr:title", "text: - ", "cr:category"]

// Complex combination
text: ["text:Order #", "uid", "text: by ", "profile:username", "text: on ", "dt:today"]

// Multiple dynamic values
text: ["text:You have ", "cr:count", "text: items in ", "cr:location", "text: warehouse"]

// With date/time
text: ["text:Last updated: ", "cdt"]

// With global variables
text: ["text:App version: ", "gv:appVersion"]

// Multiple sentences
text: ["pt", "text: | ", "ps", "text: | Updated: ", "dt:today"]
```

---

## Variable Text Feature Flags

Text arrays can contain multiple select types, each with its own `VariableSelectFeatureFlag`. When parsing text arrays, each select string is converted to a `DefaultVariableResult` with the appropriate flag, which is then embedded in the text structure.

**Note:** Text arrays use the same `VariableSelectFeatureFlag` values as [select format](select.md), since they store `DefaultVariableResult` objects. The flags are identical to those used in select format.

### Flag Mapping

Each select type in a text array maps to a `VariableSelectFeatureFlag` value (same as select format):

| Format Prefix | Flag | Flag Value | Description |
|--------------|------|------------|-------------|
| `text:` | `CustomText` | `2048` | Simple text value (rendered as plain text node `{ text: string }`) |
| `profile:` | `ProfileData` | `2` | User profile data |
| `sc:` | `SingleCell` | `4` | Specific table cell |
| `cr:` | `CurrentRow` | `4096` | Current row column value |
| `image:` | `Image` | `128` | Image URL |
| `file:` | `File` | `8192` | File URL |
| `icon:` | `Icon` | `8` | Icon value |
| `rc:` | `RichText` | `32` | Markdown content |
| `pc` | `PageCover` | `262144` | Page cover image |
| `pt` | `PageTitle` | `1024` | Page title |
| `pl` | `PageLabel` | `1024` | Page label (uses PageTitle flag) |
| `ps` | `PageSubtitle` | `2048` | Page subtitle (uses CustomText flag) |
| `dt:` | `DateTime` | `65536` | Predefined date/time |
| `cdt` | `CurrentDateTime` | `131072` | Current date and time |
| `sid` | `SessionID` | `524288` | Session identifier |
| `uid` | `UniqueID` | `2097152` | Unique identifier |
| `gv:` | `GlobalVariable` | `4194304` | Global app variable |

### Text Structure

When parsed, a text array becomes a `VariableTextValue` structure:

```typescript
type VariableTextValue = Array<{
  type: 'paragraph'
  children: Array<{ text: string } | DefaultVariableResult>
}>
```

- **Plain text nodes**: When a `text:` select is used, it's converted to `{ text: string }` for direct rendering
- **Variable nodes**: Other select types become `DefaultVariableResult` objects with their respective flags
- **Paragraph structure**: All children are wrapped in a paragraph element

### Example Structure

For the input:
```typescript
["text:Hello ", "profile:username", "text:!"]
```

The parsed structure becomes:
```typescript
[{
  type: 'paragraph',
  children: [
    { text: 'Hello ' },
    { id: '', flag: 2, col: 'username', userSpecific: false }, // ProfileData
    { text: '!' }
  ]
}]
```

**Note:** Flags are bitwise values. The parser automatically sets the correct flag based on the format prefix in each select string.
