# Data Select Documentation

## Overview

The data select component allows users to choose values from various sources including text, user profiles, table data, page metadata, dates, and global variables.

---

## Select Types

### Text (`text:`)
Simple text value.

**Syntax:** `text:<value>`

**Example:**
```typescript
select: "text:Hello World"
```

---

### Profile (`profile:`)
User profile related data.

**Syntax:** `profile:<col-id>`

**Example:**
```typescript
select: "profile:username"
select: "profile:email"
```

---

### Single Cell (`sc:`)
Single cell value from a specific table row and column.

**Syntax:** `sc:<table-id>:<col-id>:<row-number>`

**Example:**
```typescript
select: "sc:users:name:5"
select: "sc:products:price:12"
```

---

### Current Row (`cr:`)
Current row value from a table, list, or card.

**Syntax:** `cr:<col-id>`

**Example:**
```typescript
select: "cr:title"
select: "cr:status"
```

---

### Image (`image:`)
Image URL.

**Syntax:** `image:<image-url>`

**Example:**
```typescript
select: "image:https://example.com/photo.jpg"
select: "image:/assets/logo.png"
```

---

### File (`file:`)
File URL.

**Syntax:** `file:<file-url>`

**Example:**
```typescript
select: "file:https://example.com/document.pdf"
select: "file:/downloads/report.xlsx"
```

---

### Icon (`icon:`)
Icon value.

**Syntax:** `icon:<icon-value>`

**Example:**
```typescript
select: "icon:home"
select: "icon:user"
```

---

### Rich Text (`rc:`)
Markdown formatted content.

**Syntax:** `rc:<markdown-content>`

**Example:**
```typescript
select: "rc:**Bold text** and *italic*"
select: "rc:# Heading\n\nParagraph text"
```

---

### Page Cover (`pc`)
Page cover image.

**Syntax:** `pc`

**Example:**
```typescript
select: "pc"
```

---

### Page Title (`pt`)
Page title.

**Syntax:** `pt`

**Example:**
```typescript
select: "pt"
```

---

### Page Label (`pl`)
Page label.

**Syntax:** `pl`

**Example:**
```typescript
select: "pl"
```

---

### Page Subtitle (`ps`)
Page subtitle.

**Syntax:** `ps`

**Example:**
```typescript
select: "ps"
```

---

### Date Time (`dt:`)
Predefined date/time values.

**Syntax:** `dt:<date-option>`

**Available options:**
- `now` - Current date and time
- `today` - Today's date
- `tomorrow` - Tomorrow's date
- `yesterday` - Yesterday's date
- `current-month` - Current month
- `last-month` - Previous month
- `next-month` - Next month
- `current-year` - Current year
- `last-year` - Previous year
- `next-year` - Next year

**Example:**
```typescript
select: "dt:now"
select: "dt:today"
select: "dt:next-month"
```

---

### Current Date Time (`cdt`)
Current date and time (dynamic).

**Syntax:** `cdt`

**Example:**
```typescript
select: "cdt"
```

---

### Session ID (`sid`)
Current session identifier.

**Syntax:** `sid`

**Example:**
```typescript
select: "sid"
```

---

### Unique ID (`uid`)
Unique identifier.

**Syntax:** `uid`

**Example:**
```typescript
select: "uid"
```

---

### Global Variable (`gv:`)
Global variable accessible across the app.

**Syntax:** `gv:<variable-name>`

**Example:**
```typescript
select: "gv:userTheme"
select: "gv:appVersion"
```

---

---

## Variable Select Feature Flags

Each select type maps to a specific `VariableSelectFeatureFlag` value. These flags are used internally to identify the data source type.

| Format Prefix | Flag | Flag Value | Description |
|--------------|------|------------|-------------|
| `text:` | `CustomText` | `2048` | Simple text value |
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

**Note:** Flags are bitwise values that can be combined. The parser automatically sets the correct flag based on the format prefix.

---

## Select Reference

| Type | Syntax | Description | Flag |
|------|--------|-------------|------|
| Text | `text:<value>` | Simple text value | `CustomText` (2048) |
| Profile | `profile:<col-id>` | User profile data | `ProfileData` (2) |
| Single Cell | `sc:<table-id>:<col-id>:<row-number>` | Specific table cell | `SingleCell` (4) |
| Current Row | `cr:<col-id>` | Current row column value | `CurrentRow` (4096) |
| Image | `image:<image-url>` | Image URL | `Image` (128) |
| File | `file:<file-url>` | File URL | `File` (8192) |
| Icon | `icon:<icon-value>` | Icon value | `Icon` (8) |
| Rich Text | `rc:<markdown-content>` | Markdown content | `RichText` (32) |
| Page Cover | `pc` | Page cover image | `PageCover` (262144) |
| Page Title | `pt` | Page title | `PageTitle` (1024) |
| Page Label | `pl` | Page label | `PageTitle` (1024) |
| Page Subtitle | `ps` | Page subtitle | `CustomText` (2048) |
| Date Time | `dt:<date-option>` | Predefined date/time | `DateTime` (65536) |
| Current Date Time | `cdt` | Current date and time | `CurrentDateTime` (131072) |
| Session ID | `sid` | Session identifier | `SessionID` (524288) |
| Unique ID | `uid` | Unique identifier | `UniqueID` (2097152) |
| Global Variable | `gv:<variable-name>` | Global app variable | `GlobalVariable` (4194304) |