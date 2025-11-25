# Makyo AI JSON Documentation

### Mandatory JSON Design Rules

#### 1. JSON Structure

- **Wrapper**: The output must always start with `[` and close with `]`.

---

#### 2. Colors & Tokens

- **Valid Tone Range**: Only use color tokens with tones from **10 to 100** (e.g., `neutral-10`, `primary-90`). Tones `0` and `5` are forbidden.
- **Palettes**: Use only `primary`, `secondary`, `tertiary`, and `neutral`.
- **No Hardcoding**: Never use hex codes (e.g., `#FF0000`) or raw color names.
- **Text & Button Default**: Text color (`color`) and button background color (`backgroundColor`) must default to `"adaptive"`.
- **Transparency (No Background on Children)**: To assign 'no color' to a section background when it has a parent section, explicitly use `"background": ["color:transparent"]`.

---

#### 3. Spacing Constraints

- **Text Components**:
  - Margin must be `m:0px`.
  - Padding must be `p:0px`.
- **Form Components**: Padding must be `p:0px`.
- **Section Item Gap**: Must be `gap:10px`.
- **General Margins**: For all components (except Text), the `margin` property should generally be left empty `""`.

---

#### 4. Section Layout & Responsive Syntax

- **Orientation Syntax**: Always use abbreviations `"h"` (horizontal) and `"v"` (vertical).
- **Responsive Syntax (Explicit Breakpoints)**: When using responsive styles, **specify the property for each screen size** (`ph`, `pl`, `ta`, `tl`, `de`, `tv`), with no shortcuts.
- **Parent Section Orientation**: The main layout-defining section (any section with child sections) must use the explicit orientation map: `ph:v pl:h ta:h tl:h de:h tv:h`.
- **Content Restriction**: For standard content on Desktop (`de:`) and TV (`tv`), width must be restricted to 40%, 50%, or 60% (e.g., `w:100% de:w:60%`).
- **Responsive Columns (Strategy)**:
  - **Portrait (Mobile/Tablet)**: Stacked (`cols:100`, orientation: `"v"`).
  - **Landscape/Desktop**: Split Columns (e.g., `cols:50:50`, orientation: `"h"`).

---

#### 5. Section Logic (Shape vs. Margin)

- **Forbidden Combination**: You cannot have a section with both `margin: ""` AND `shape: "none"`.
- **Rule**: If a section has no margin, it must have a shape. If a section has no shape, it must have a margin.

---

#### 6. Text, Button & Image Rules

- **Image Source (Unsplash)**: Always provide a matching image URL from **Unsplash** instead of a placeholder or local file name.
- **Button Alignment**: Button horizontal alignment (e.g., `h:center`) must match the preceding text's alignment (e.g., `t:center`).
- **Image Title**: **DO NOT** include the `imageTitle` property.
  message.txt
  3 KB
