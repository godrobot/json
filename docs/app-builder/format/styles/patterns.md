# Pattern System Documentation

## Overview

The Makyo pattern system provides decorative background patterns for elements. Patterns can be customized with color, opacity, and size configurations.

---

## Pattern Syntax

**Syntax:** `<pattern>:<color>:<opacity>:<size>`

**Properties:**
1. **Pattern** - Pattern name (see available patterns below)
2. **Color** - Color value (e.g., `primary-40`, `neutral-20`, `secondary-60`)
3. **Opacity** - Opacity value from `0` to `1` (0 = transparent, 1 = opaque)
4. **Size** - Size value from `16` to `96` (pattern scale)

**Examples:**
```typescript
// Pattern with color, opacity, and size
pattern: "Circle1:primary-40:0.5:32"

// Different pattern variations
pattern: "Stripe1:neutral-20:0.3:24"
pattern: "Dot2:secondary-60:0.8:48"
pattern: "Wave:primary-80:0.6:40"
```

---

## Available Patterns

### Circle Patterns
`Circle1`, `Circle2`, `Circle3`, `Circle4`, `Circle5`, `Circle6`, `Circle7`, `Circle8`, `Circle9`, `Circle10`, `Circle11`, `Circle12`

### Cross Patterns
`Cross1`, `Cross2`, `Cross3`, `Cross4`

### Diagonal Patterns
`Diagonal1`, `Diagonal2`, `Diagonal3`, `Diagonal4`, `Diagonal5`

### Diamond Patterns
`Diamond1`, `Diamond2`, `Diamond3`, `Diamond4`, `Diamond5`, `Diamond6`, `Diamond7`, `Diamond8`, `Diamond9`

### Dot Patterns
`Dot1`, `Dot2`, `Dot3`, `Dot4`

### Line Patterns
`Line1`, `Line2`, `Line3`, `Line4`, `Line5`, `Line6`, `Line7`, `Line8`, `Line9`, `Line10`

### Mixed Patterns
`Mixed1`, `Mixed2`, `Mixed3`, `Mixed4`, `Mixed5`, `Mixed6`, `Mixed7`, `Mixed8`, `Mixed9`, `Mixed10`, `Mixed11`, `Mixed12`, `Mixed13`, `Mixed14`

### Stripe Patterns
`Stripe1`, `Stripe2`, `Stripe3`, `Stripe4`, `Stripe5`, `Stripe6`

### Symbol Patterns
`Symbol1`, `Symbol2`

### Triangle Patterns
`Triangle1`, `Triangle2`, `Triangle3`, `Triangle4`, `Triangle5`, `Triangle6`, `Triangle7`

### Wave & Zigzag Patterns
`Wave`, `Zigzag`

### No Pattern
`No Pattern` - Removes any applied pattern

---

## Examples

```typescript
// Circle pattern
pattern: "Circle1:primary-40:0.5:32"

// Stripe pattern with low opacity
pattern: "Stripe1:neutral-20:0.2:24"

// Dot pattern with high opacity
pattern: "Dot2:secondary-60:0.8:48"

// Wave pattern
pattern: "Wave:primary-80:0.6:40"

// Diamond pattern
pattern: "Diamond1:secondary-30:0.4:36"

// No pattern (removes pattern)
pattern: ""
```

---

## Pattern Reference

| Property | Position | Values | Description |
|----------|----------|--------|-------------|
| Pattern | 1 | Pattern names (see above) | Pattern style |
| Color | 2 | Color values (e.g., `primary-40`) | Pattern color |
| Opacity | 3 | `0`-`1` | Pattern transparency |
| Size | 4 | `16`-`96` | Pattern scale |
