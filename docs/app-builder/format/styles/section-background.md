# Section Background Documentation

## Overview

Section backgrounds support multiple layers that are rendered visually from bottom to top. Each layer can be configured independently, allowing for complex visual effects by combining colors, images, videos, patterns, overlays, effects, and masks.

---

## Background Layers

Background layers are specified in the array from top to bottom (first item = top layer, last item = bottom layer). The layers are automatically sorted so that:

- **Overlay** is rendered on top (highest priority)
- **Color** is rendered at the bottom (lowest priority)

**Supported Layer Types (priority order from top to bottom):**

1. **Overlay** - Color overlay with opacity (rendered on top)
2. **Mask** - Mask overlay with responsive values
3. **Effect** - Animated effects (gradient, particles, etc.)
4. **Video** - YouTube video or video URL background
5. **Image** - Background image with optional parallax effect
6. **Pattern** - Pattern overlay (circles, lines, etc.)
7. **Color** - Base color layer (solid, gradient, or adaptive) (rendered at bottom)

---

## Background Format

Background is specified as an array of layer strings. Each string represents one layer, making it more readable and avoiding conflicts with `|` used in adaptive colors.

**Syntax:**

```typescript
background: string[]
```

**Multiple Layers Format:**
Each layer is a separate string in the array:

- `["color:solid:primary-40", "image:url", "overlay:#000000:0.5"]` - Multiple layers

**Examples:**

```typescript
// Simple solid color background
background: ['solid:primary-40']

// Transparent background (No Color)
background: ['transparent']
background: ['color:transparent']

// Empty background (no layers, uses default template layers)
background: []

// Gradient background
background: ['gradient:primary-40|primary-80:to-right']

// Color with image (order doesn't matter - automatically sorted)
background: ['image:https://example.com/bg.jpg', 'color:solid:primary-40']

// Color with image using variable select
background: ['image:sc:products:coverImage:5', 'color:solid:primary-40']

// Color with image and overlay (ordered from top to bottom: overlay first, color last)
background: [
  'overlay:#000000:0.5', // Top layer
  'image:https://example.com/bg.jpg', // Middle layer
  'color:gradient:primary-40|primary-80:to-right', // Bottom layer
]

// Complex multi-layer background (ordered from top to bottom)
background: [
  'overlay:#000000:0.3:enabled', // Top layer
  'pattern:Circle1:0.1:primary-10', // Upper middle
  'image:https://example.com/bg.jpg:parallax', // Lower middle
  'color:adaptive:primary-80|primary-100', // Bottom layer
]

// Color with video (URL defaults to text: format, flag 2048)
background: ['video:text:https://www.youtube.com/watch?v=VIDEO_ID', 'color:solid:primary-40']

// Color with video using variable select
background: ['video:cr:videoUrl', 'color:solid:primary-40']

// Color with video and flags (loop and muted)
background: ['video:text:https://www.youtube.com/watch?v=VIDEO_ID:loop:muted', 'color:solid:primary-40']

// Color with effect
background: ['effect:gradient:primary-40,secondary-60,tertiary-80:neutral-100:100:100', 'color:solid:neutral-100']
```

---

## Layer Types Reference

### Color Layer

Base color layer supporting solid colors, gradients, adaptive colors, and transparent backgrounds.

**Format:** `color:<color-format>` or `<color-format>` (simple format)

**Color Formats:**

- `solid:<color>` - Solid color (e.g., `solid:primary-40`)
- `gradient:<color1>|<color2>:<direction>` - Gradient (e.g., `gradient:primary-40|primary-80:to-right`)
- `adaptive:<light-color> <dark-color>` - Adaptive color for light/dark modes (e.g., `adaptive:primary-40 primary-80`)
- `transparent` - Transparent background (no color)

**Examples:**

```typescript
// Solid color
color:solid:primary-40
solid:primary-40

// Gradient
color:gradient:primary-40|primary-80:to-right
gradient:primary-40|primary-80:to-right

// Adaptive color
color:adaptive:primary-40 primary-80
adaptive:primary-40 primary-80

// Transparent background
color:transparent
transparent
```

See [Color Format Documentation](./colors.md) for full color format details.

---

### Image Layer

Background image with optional parallax scrolling effect and animation types. Supports variable select format for dynamic image sources.

**Format:** `image:<url>` or `image:<url>:parallax` or `image:<variable-select>`

**Parameters:**

- `url` - Image URL or variable select format (see [Variable Select Documentation](../data/select.md))
  - Simple URLs default to `image:` format (flag 128 - Image)
  - Variable select formats: `sc:table:col:row`, `cr:title`, `text:value`, `pc`, etc.
- `parallax` (optional) - Enable parallax effect (`parallax` or `true`)

**Animation Types** (configured via JSON settings):

- `none` - No animation (default)
- `parallax` - Parallax scrolling effect
- `ken-burns` - Ken Burns zoom effect
- `fade` - Fade animation
- `zoom` - Zoom animation
- `pan` - Pan animation

**Note:** Animation types (`animationType`, `animationSpeed`, `animationDuration`) are configured through the component settings JSON, not through the format string.

**Examples:**

```typescript
// Simple URL (defaults to image: format, flag 128)
image: //example.com/image.jpg
https: image: //example.com/image.jpg:parallax

// Variable select formats
https: image: text: //example.com/image.jpg
https: image: sc: products: imageUrl: 5
image: cr: coverImage
image: pc // Page cover
```

---

### Video Layer

YouTube video or video URL background. Supports variable select format for dynamic video sources.

**Format:** `video:<url>` or `video:<url>:loop:muted` or `video:<variable-select>`

**Parameters:**

- `url` - Video URL or variable select format (see [Variable Select Documentation](../data/select.md))
  - Simple URLs default to `text:` format (flag 2048 - CustomText)
  - Variable select formats: `sc:table:col:row`, `cr:title`, `text:value`, etc.
- `loop` (optional) - Enable looping (`loop` or `true`, default: `true`)
- `muted` (optional) - Mute video (`muted` or `true`, default: `true`)

**Examples:**

```typescript
// Simple URL (defaults to text: format, flag 2048)
// When formatted, URLs with flag 2048 include the "text:" prefix
video:text:https://www.youtube.com/watch?v=VIDEO_ID
video:text:https://example.com/video.mp4:loop:muted

// Variable select formats
video:text:https://www.youtube.com/watch?v=VIDEO_ID:loop:muted
video:sc:videos:videoUrl:3:loop:muted
video:cr:videoLink:loop:muted

// Note: When parsing, both formats are supported:
//   - video:text:https://... (explicit variable select)
//   - video:https://... (simple URL, automatically wrapped in text: format)
```

---

### Overlay Layer

Color overlay with opacity, typically used to darken or tint backgrounds.

**Format:** `overlay:<color>:<opacity>` or `overlay:<color>:<opacity>:enabled`

**Parameters:**

- `color` - Overlay color (hex format, e.g., `#000000`)
- `opacity` - Opacity value (0.0 to 1.0)
- `enabled` (optional) - Enable overlay (`enabled` or `true`, default: `true`)

**Examples:**

```typescript
overlay:#000000:0.5
overlay:#000000:0.5:enabled
overlay:#FF0000:0.3
```

---

### Pattern Layer

Pattern overlay (circles, lines, etc.) with opacity and color.

**Format:** `pattern:<type>:<opacity>:<color>`

**Parameters:**

- `type` - Pattern type (e.g., `Circle1`, `Lines`, etc.)
- `opacity` - Pattern opacity (0.0 to 1.0)
- `color` - Pattern color (color variant, e.g., `primary-10`)

**Examples:**

```typescript
pattern:Circle1:0.1:primary-10
pattern:Lines:0.2:neutral-20
```

---

### Effect Layer

Animated background effects (gradient animations, particles, etc.).

**Format:** `effect:<type>:<colors>:<bgColor>:<speed>:<opacity>`

**Parameters:**

- `type` - Effect type (see available types below)
- `colors` - Comma-separated list of color variants (ColorVariant format, e.g., `primary-40,secondary-60,tertiary-80`)
- `bgColor` - Background color (ColorVariant format, e.g., `neutral-100`)
- `speed` - Animation speed (0-200, optional, default: `100`)
- `opacity` - Effect opacity (0-100, optional, default: `100`)

**Available Effect Types:**

- `none` - No effect (default)
- `gradient` - Static gradient
- `animated-gradient` - Animated gradient
- `beams` - Beam effects
- `wavy` - Wavy animation
- `sparkles` - Sparkle particles
- `flicker-grid` - Flickering grid
- `meteors` - Meteor shower
- `stars` - Starfield
- `boxes` - Animated boxes
- `aurora` - Aurora effect
- `paths` - Animated paths
- `fluid-gradient` - Fluid gradient animation
- `shader-clouds` - Shader-based clouds
- `orbs` - Orb particles
- `dot-matrix` - Dot matrix pattern
- `spotlight` - Spotlight effect
- `noise` - Noise texture
- `mesh-gradient` - Mesh gradient
- `ripple-waves` - Ripple waves
- `floating-bubbles` - Floating bubbles
- `neural-network` - Neural network visualization
- `matrix-rain` - Matrix rain effect
- `particles-flow` - Particle flow

**Examples:**

```typescript
// Gradient effect
effect:gradient:primary-40,secondary-60,tertiary-80:neutral-100:100:100

// Animated gradient
effect:animated-gradient:primary-40,secondary-60,tertiary-80:neutral-100:150:80

// Particle effects
effect:sparkles:neutral-0:neutral-100:50:80
effect:meteors:primary-40:neutral-100:75:90

// Advanced effects
effect:aurora:primary-20,secondary-40:neutral-100:100:100
effect:fluid-gradient:primary-40,secondary-60,tertiary-80:neutral-95:120:85
```

---

### Mask Layer

Mask overlay with responsive values. Note: Full responsive mask configuration is complex and may require direct JSON configuration.

**Format:** `mask:<type>:<opacity>` (simplified)

**Parameters:**

- `type` - Mask type (e.g., `#` for hash pattern, SVG path for custom masks)
- `opacity` - Mask opacity (0.0 to 1.0)

**Examples:**

```typescript
mask:#:0.75
mask:/mask/waves.svg:0.5
```

**Note:** For full responsive mask configuration with different values per breakpoint, you may need to configure the background directly in JSON format.

---

## Layer Rendering Order

Layers are specified in the array from top to bottom (first item = top layer, last item = bottom layer). Visually, layers are rendered from bottom to top:

```
Bottom Layer (rendered first, specified last in array)
  ↓
  ↓
Top Layer (rendered last, specified first in array)
```

**Example:**

```typescript
background: [
  'overlay:#000:0.5', // Top layer (rendered last)
  'image:url', // Middle layer
  'color:solid:primary-40', // Bottom layer (rendered first)
]
```

Visual rendering order (bottom to top):

1. Color layer (bottom - specified last in array)
2. Image layer (middle)
3. Overlay layer (top - specified first in array)

---

## Complete Examples

```typescript
// Empty background (no layers, uses default template layers)
background: []

// Simple solid color background
background: ['solid:primary-40']

// Gradient background
background: ['gradient:primary-40|primary-80:to-right']

// Color with image (order doesn't matter - automatically sorted)
background: ['image:https://example.com/bg.jpg', 'color:solid:primary-40']

// Color with image using variable select
background: ['image:cr:coverImage', 'color:solid:primary-40']

// Complex multi-layer background (ordered from top to bottom)
background: [
  'overlay:#000000:0.3:enabled', // Top layer
  'pattern:Circle1:0.1:primary-10', // Upper middle
  'image:https://example.com/bg.jpg', // Lower middle
  'color:gradient:primary-40|primary-80:to-right', // Bottom layer
]

// Video background with overlay (ordered from top to bottom)
background: [
  'overlay:#000000:0.4', // Top layer
  'video:text:https://www.youtube.com/watch?v=VIDEO_ID:loop:muted', // Middle layer
  'color:solid:#000000', // Bottom layer
]

// Video background with variable select (ordered from top to bottom)
background: [
  'overlay:#000000:0.4', // Top layer
  'video:sc:videos:youtubeUrl:2:loop:muted', // Middle layer
  'color:solid:#000000', // Bottom layer
]

// Effect background (ordered from top to bottom)
background: [
  'effect:gradient:primary-40,secondary-60,tertiary-80:neutral-100:100:100', // Top layer
  'color:solid:neutral-100', // Bottom layer
]
```

---

## Notes

- Layers are specified in the array from top to bottom (first item = top layer, last item = bottom layer)
- Layers are automatically sorted by type priority (overlay on top, color at bottom)
- Layer IDs are automatically assigned based on the sorted order
- Lower IDs are rendered first (underneath)
- Higher IDs are rendered on top
- If a layer type doesn't exist in the template, it will be skipped
- Simple color format (without `color:` prefix) is backward compatible and only affects the color layer
- For complex responsive configurations (especially masks), consider using direct JSON configuration
