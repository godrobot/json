# Corner Radius System Documentation

## Overview

The Makyo corner radius system controls the roundness of element corners. It supports responsive configurations across different breakpoints.

---

## Corner Radius

**Syntax:** `<value>`

**Available values:**
- `none` - No rounding (sharp corners)
- `extra-small` - Minimal rounding
- `small` - Subtle rounding
- `medium` - Moderate rounding
- `large` - Pronounced rounding
- `extra-large` - Very rounded corners
- `full` - Fully rounded (pill/circle shape)

**Examples:**
```typescript
radius: "none"
radius: "small"
radius: "medium"
radius: "full"
```

---

## Responsive Corner Radius

Corner radius can be configured differently for each [breakpoint](breakpoints.md) by prefixing with a breakpoint abbreviation.

**Syntax:**
```
<value> <breakpoint>:<value> <breakpoint>:<value>
```

**Examples:**
```typescript
// Different radius on different screens
radius: "small ta:medium de:large"

// Sharp on mobile, rounded on larger screens
radius: "none ta:small de:medium"

// Fully rounded on all screens except desktop
radius: "full de:medium"
```

---

## Corner Radius Reference

| Value | Description |
|-------|-------------|
| `none` | No rounding (sharp corners) |
| `extra-small` | Minimal rounding |
| `small` | Subtle rounding |
| `medium` | Moderate rounding |
| `large` | Pronounced rounding |
| `extra-large` | Very rounded corners |
| `full` | Fully rounded (pill/circle shape) |
