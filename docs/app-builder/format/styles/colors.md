# Color System Documentation

## Overview

The Makyo color system supports three types of color configurations: adaptive, solid, and gradient. This flexible system allows you to define different color schemes for light and dark modes.

---

## Color Types

- adaptive
- solid
- gradient

### Adaptive

Automatically adjusts based on the system theme.

**Syntax:** `adaptive`

### Solid

A single, uniform color value.

**Syntax:** `solid:<color-value>`

**Example:** `solid:primary-40`

### Gradient

A smooth transition between two or more colors in a specified direction.

**Syntax:** `gradient:<color-1>|<color-2>:<direction>`

**Example:** `gradient:primary-40|primary-80:to-right`

---

## Gradient Directions

Gradients support the following directional values:

| Direction         | Description                        |
| ----------------- | ---------------------------------- |
| `to-right`        | Left to right                      |
| `to-left`         | Right to left                      |
| `to-top`          | Bottom to top                      |
| `to-bottom`       | Top to bottom                      |
| `to-top-right`    | Diagonal: bottom-left to top-right |
| `to-top-left`     | Diagonal: bottom-right to top-left |
| `to-bottom-right` | Diagonal: top-left to bottom-right |
| `to-bottom-left`  | Diagonal: top-right to bottom-left |

---

## Theme-Specific Colors

You can specify different colors for light and dark modes by separating them with a **space character** (` `).

### Syntax

```
<light-mode-color> <dark-mode-color>
```

### Examples

**Solid colors for light and dark modes:**

```
solid:primary-40 solid:primary-80
```

**Gradient for light mode, solid for dark mode:**

```
gradient:primary-40|primary-60:to-right solid:primary-80
```

**Different gradients for each mode:**

```
gradient:primary-20|primary-40:to-bottom gradient:primary-80|primary-100:to-top
```

---

## Usage

The color needs to be designated by a string based on the type:

- **adaptive**: `adaptive` - Automatically adjusts based on the system theme (default for many components)
- **solid**: `solid:primary-40` where _primary-40_ is the value of the color
- **gradient**: `gradient:primary-40|primary-80:to-right` where _primary-40_ and _primary-80_ are the values of the colors, and _to-right_ is the direction of the gradient.

Light and dark mode colors can be specified by separating them with a space (` `):
For example:
`solid:primary-40 gradient:primary-40|primary-80:to-right` for light and dark mode respectively.

**Note:** When using `adaptive`, the system automatically handles theme switching and color inversion. This is the recommended default for most components as it ensures proper contrast and readability in both light and dark themes.

### Single Mode Configuration

```typescript
// Adaptive color (automatically adjusts)
color: 'adaptive'

// Solid color
color: 'solid:primary-40'

// Gradient
color: 'gradient:primary-40|primary-80:to-right'
```

### Dual Mode Configuration

```typescript
// Light mode: solid, Dark mode: gradient
color: 'solid:primary-40 gradient:primary-40|primary-80:to-right'

// Light mode: horizontal gradient, Dark mode: vertical gradient
color: 'gradient:accent-20|accent-60:to-right gradient:accent-80|accent-100:to-bottom'
```

---

## Best Practices

1. **Use adaptive colors** when you want the system to handle theme switching automatically
2. **Provide both light and dark variants** for better user experience across themes
3. **Choose appropriate gradient directions** that complement your UI layout
4. **Maintain consistent color values** across your application using your design system tokens

---

## Color Token System

### Overview

The Makyo color system uses a token-based approach where colors are organized into **palettes** and **tones**. Each color token follows the pattern `<palette>-<tone>` (e.g., `primary-40`, `secondary-60`).

### Available Color Palettes

The system provides four main color palettes:

1. **Primary** - The main brand color palette
2. **Secondary** - A complementary color palette
3. **Tertiary** - An additional accent color palette
4. **Neutral** - Grayscale palette for text, borders, and backgrounds

### Available Color Tones

Each palette includes the following tone levels:

| Tone  | Description  | Usage                              |
| ----- | ------------ | ---------------------------------- |
| `0`   | Pure white   | Lightest possible tone             |
| `5`   | Very light   | Subtle backgrounds, highlights     |
| `10`  | Light        | Light backgrounds, subtle elements |
| `20`  | Light-medium | Backgrounds, cards                 |
| `30`  | Medium-light | Borders, dividers                  |
| `40`  | Medium       | Primary brand colors, buttons      |
| `50`  | Medium-dark  | Secondary elements                 |
| `60`  | Dark-medium  | Text, emphasis                     |
| `70`  | Dark         | Headings, important text           |
| `80`  | Very dark    | Strong contrast elements           |
| `90`  | Darkest      | Maximum contrast                   |
| `95`  | Near black   | Almost black                       |
| `100` | Pure black   | Darkest possible tone              |

### Important: Tone Inversion in Dark/Light Themes

**⚠️ Critical Understanding:** The tone values are **inverted** between light and dark themes. This means:

- **Light Theme:** Lower tones (0-40) are lighter colors, higher tones (60-100) are darker colors
- **Dark Theme:** Lower tones (0-40) are darker colors, higher tones (60-100) are lighter colors

**Example:**

- `primary-40` in **light mode** = medium brightness (typical brand color)
- `primary-40` in **dark mode** = darker appearance (automatically adjusted)
- `primary-80` in **light mode** = very dark color
- `primary-80` in **dark mode** = lighter color (for contrast)

This inversion ensures proper contrast and readability in both themes. When using `adaptive` color mode, the system automatically handles this inversion.

### Complete Color Token List

#### Primary Palette

```
primary-0, primary-5, primary-10, primary-20, primary-30, primary-40,
primary-50, primary-60, primary-70, primary-80, primary-90, primary-95, primary-100
```

#### Secondary Palette

```
secondary-0, secondary-5, secondary-10, secondary-20, secondary-30, secondary-40,
secondary-50, secondary-60, secondary-70, secondary-80, secondary-90, secondary-95, secondary-100
```

#### Tertiary Palette

```
tertiary-0, tertiary-5, tertiary-10, tertiary-20, tertiary-30, tertiary-40,
tertiary-50, tertiary-60, tertiary-70, tertiary-80, tertiary-90, tertiary-95, tertiary-100
```

#### Neutral Palette

```
neutral-0, neutral-5, neutral-10, neutral-20, neutral-30, neutral-40,
neutral-50, neutral-60, neutral-70, neutral-80, neutral-90, neutral-95, neutral-100
```

### Using Color Tokens in AI JSON

When generating component JSON structures, always use color tokens instead of hex codes or arbitrary color names. The AI should recognize and provide these tokens in the format:

**Format:** `<palette>-<tone>`

**Examples:**

```json
{
  "type": "button",
  "backgroundColor": "solid:primary-40",
  "badgeColor": "solid:secondary-60"
}
```

```json
{
  "type": "text",
  "color": "solid:neutral-90"
}
```

```json
{
  "type": "section",
  "background": "gradient:primary-40|primary-80:to-right"
}
```

### Common Color Token Patterns

#### For Backgrounds

- Common backgrounds: `primary-95`, `secondary-95`, `tertiary-95`, `neutral-95`
- Light backgrounds: `primary-5`, `primary-10`, `neutral-5`, `neutral-10`
- Medium backgrounds: `primary-20`, `primary-30`, `neutral-20`
- Dark backgrounds: `primary-80`, `primary-90`, `neutral-80`, `neutral-90`

#### For Main Color Accents

- Primary brand accents: `primary-20`, `primary-30`, `primary-40`
- Secondary accents: `secondary-20`, `secondary-30`, `secondary-40`
- Tertiary accents: `tertiary-20`, `tertiary-30`, `tertiary-40`

#### For Text

- Light text on dark backgrounds: `neutral-0`, `neutral-5`, `primary-5`
- Dark text on light backgrounds: `neutral-90`, `neutral-100`, `primary-90`
- Medium contrast: `neutral-70`, `neutral-80`

#### For Interactive Elements

- Primary buttons: `primary-20`, `primary-30`, `primary-40`
- Secondary buttons: `secondary-20`, `secondary-30`, `secondary-40`
- Hover states: `primary-50`, `secondary-50`
- Active states: `primary-60`, `secondary-60`

#### For Borders and Dividers

- Light borders: `neutral-10`, `neutral-20`
- Medium borders: `neutral-30`, `neutral-40`
- Dark borders: `neutral-60`, `neutral-70`

### AI Recognition Guidelines

When generating component JSON, the AI should:

1. **Always use color tokens** - Never use hex codes (`#FF5733`), RGB values, or arbitrary color names (`"red"`, `"blue"`)
2. **Use appropriate tones** - Choose tones that match the context (lighter for backgrounds, darker for text)
3. **Understand tone inversion** - Remember that tones are inverted between light and dark themes
4. **Maintain consistency** - Use the same palette family for related elements
5. **Consider contrast** - Ensure sufficient contrast between foreground and background colors
6. **Use semantic naming** - Prefer `primary-40` over `primary-50` for main brand colors
7. **Prefer adaptive mode** - When possible, use `adaptive` to let the system handle theme switching automatically

### Examples in Component JSON

```json
{
  "type": "button",
  "backgroundColor": "solid:primary-40",
  "label": ["text:Click Me"]
}
```

```json
{
  "type": "section",
  "background": "gradient:primary-20|primary-40:to-bottom",
  "children": []
}
```

---

## Color Value Reference (Legacy)

Color values (e.g., `primary-40`, `secondary-60`) reference the design system's color palette. The numeric suffix indicates the tone level, where:

- Lower numbers (e.g., `20`, `40`) = lighter tones (in light theme) / darker tones (in dark theme)
- Higher numbers (e.g., `80`, `100`) = darker tones (in light theme) / lighter tones (in dark theme)

**Note:** Tone values are inverted between light and dark themes to maintain proper contrast.
