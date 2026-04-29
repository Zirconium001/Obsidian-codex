# 🎨 CSS Complete Reference Notes

> A structured documentation of CSS — from basics to advanced topics.

---

## Table of Contents

- [🎯 What is CSS](#-what-is-css)
- [🧩 CSS Syntax](#-css-syntax)
- [🎯 Selectors](#-selectors)
- [🎨 Colors & Units](#-colors--units)
- [🔤 Typography](#-typography)
- [📦 Box Model](#-box-model)
- [📐 Layout & Display](#-layout--display)
- [📏 Positioning](#-positioning)
- [🧱 Flexbox](#-flexbox)
- [🧮 CSS Grid](#-css-grid)
- [🖼️ Backgrounds](#️-backgrounds)
- [✨ Effects & Shadows](#-effects--shadows)
- [🎞️ Transitions & Animations](#️-transitions--animations)
- [📱 Responsive Design](#-responsive-design)
- [⚙️ Variables & Functions](#️-variables--functions)
- [🧠 Best Practices](#-best-practices)

---

## 🎯 What is CSS

CSS (Cascading Style Sheets) controls the **appearance** of HTML elements.

| Layer | Role |
|-------|------|
| HTML | Structure |
| CSS | Style |
| JS | Behavior |

### Ways to Add CSS

**1️⃣ Inline CSS**

```html
<p style="color: red;">Hello</p>
```

**2️⃣ Internal CSS**

```html
<style>
  p { color: red; }
</style>
```

**3️⃣ External CSS** ✅ Best Practice

```html
<link rel="stylesheet" href="style.css">
```

---

## 🧩 CSS Syntax

```css
selector {
  property: value;
}
```

**Example:**

```css
h1 {
  color: blue;
  font-size: 30px;
}
```

| Part | Meaning |
|------|---------|
| Selector | The HTML element to target |
| Property | What aspect to change |
| Value | How to change it |

---

## 🎯 Selectors

### Basic Selectors

```css
p { }          /* Element selector */
#title { }     /* ID selector */
.box { }       /* Class selector */
* { }          /* Universal selector */
```

### Group Selector

Applies the same styles to multiple elements.

```css
h1, h2, h3 {
  color: blue;
}
```

### Descendant & Child Selectors

```css
div p { color: red; }      /* Any <p> inside a <div> */
div > p { color: green; }  /* Direct <p> child of <div> only */
```

### Attribute Selector

```css
input[type="text"] {
  border: 1px solid black;
}
```

### Pseudo-Classes

Target elements based on their state or position.

```css
a:hover { color: red; }              /* On mouse hover */
button:active { transform: scale(.9); }  /* While being clicked */
li:first-child { color: blue; }      /* First list item */
li:last-child { color: gray; }       /* Last list item */
li:nth-child(2) { color: orange; }   /* Specific child by index */
```

### Pseudo-Elements

Target specific parts of an element.

```css
p::first-letter { font-size: 30px; }    /* First letter of paragraph */
p::before { content: "★ "; }           /* Insert content before */
p::after  { content: " ✔"; }           /* Insert content after */
```

---

## 🎨 Colors & Units

### Color Formats

```css
color: red;                  /* Named color */
color: #ff0000;              /* Hex */
color: rgb(255, 0, 0);       /* RGB */
color: rgba(255, 0, 0, 0.5); /* RGB with opacity */
color: hsl(0, 100%, 50%);    /* HSL */
```

### Units

| Type | Examples | Use Case |
|------|----------|----------|
| Absolute | `px`, `cm` | Fixed sizes |
| Relative | `%`, `em`, `rem` | Scalable sizes |
| Viewport | `vw`, `vh` | Screen-relative sizes |

```css
font-size: 2rem;    /* Relative to root font size */
width: 50%;         /* Relative to parent width */
height: 100vh;      /* Full viewport height */
padding: 1em;       /* Relative to element's font size */
```

---

## 🔤 Typography

```css
font-family: Arial, sans-serif;
font-size: 18px;
font-weight: bold;       /* or 100–900 */
font-style: italic;
line-height: 1.6;
text-align: center;      /* left | right | center | justify */
text-decoration: underline;
text-transform: uppercase;
letter-spacing: 2px;
word-spacing: 5px;
```

### 🌐 Google Web Fonts

**Step 1 — Add to HTML `<head>`:**

```html
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;700&display=swap" rel="stylesheet">
```

**Step 2 — Use in CSS:**

```css
body {
  font-family: "Poppins", sans-serif;
}
```

---

## 📦 Box Model

Every HTML element is treated as a rectangular box.

```
┌──────────────────────────┐
│         Margin           │
│  ┌────────────────────┐  │
│  │      Border        │  │
│  │  ┌──────────────┐  │  │
│  │  │   Padding    │  │  │
│  │  │  ┌────────┐  │  │  │
│  │  │  │Content │  │  │  │
│  │  │  └────────┘  │  │  │
│  │  └──────────────┘  │  │
│  └────────────────────┘  │
└──────────────────────────┘
```

```css
div {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}
```

### Box Sizing

> ✅ Always include this in your CSS reset — it makes sizing more predictable.

```css
* {
  box-sizing: border-box;
}
```

| Value | Behavior |
|-------|----------|
| `content-box` (default) | Width applies to content only |
| `border-box` | Width includes padding and border |

---

## 📐 Layout & Display

```css
display: block;         /* Full width, starts on new line */
display: inline;        /* Only takes needed width, no height/width control */
display: inline-block;  /* Inline but accepts width/height */
display: none;          /* Removes element from layout entirely */
```

### Visibility vs Display

```css
visibility: hidden;  /* Element is invisible but still takes up space */
display: none;       /* Element is removed and takes up no space */
```

---

## 📏 Positioning

```css
position: static;    /* Default — normal document flow */
position: relative;  /* Offset from its normal position */
position: absolute;  /* Positioned relative to nearest positioned parent */
position: fixed;     /* Fixed to the viewport (stays on scroll) */
position: sticky;    /* Sticks when scrolled to a threshold */
```

### Offset Properties

Used with `relative`, `absolute`, `fixed`, and `sticky`.

```css
.box {
  position: absolute;
  top: 20px;
  left: 50px;
  right: 0;
  bottom: 0;
}
```

### Z-Index (Stacking Order)

```css
.overlay {
  position: absolute;
  z-index: 10;   /* Higher value = appears on top */
}
```

> ⚠️ `z-index` only works on elements with a `position` value other than `static`.

---

## 🧱 Flexbox

One-dimensional layout system — arranges items in a **row or column**.

```css
.container {
  display: flex;
}
```

### Main Container Properties

```css
flex-direction: row;            /* row | column | row-reverse | column-reverse */
justify-content: center;        /* Main axis alignment */
align-items: center;            /* Cross axis alignment */
flex-wrap: wrap;                /* Allow items to wrap to next line */
gap: 20px;                      /* Space between items */
```

### `justify-content` Values

```css
justify-content: flex-start;    /* Default — pack to start */
justify-content: flex-end;      /* Pack to end */
justify-content: center;        /* Center items */
justify-content: space-between; /* Equal space between items */
justify-content: space-around;  /* Equal space around items */
```

### Flex Item Properties

```css
.item {
  flex: 1;          /* Grow to fill available space */
  flex-grow: 1;
  flex-shrink: 0;
  flex-basis: 200px;
  align-self: flex-end;  /* Override align-items for this item */
}
```

### ✅ Perfect Centering Example

```css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
```

---

## 🧮 CSS Grid

Two-dimensional layout system — controls both **rows and columns**.

```css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;  /* 3 equal columns */
  grid-template-rows: auto;
  gap: 20px;
}
```

### Column Sizing

```css
grid-template-columns: 200px 1fr 2fr;       /* Mixed sizes */
grid-template-columns: repeat(3, 1fr);       /* Shorthand for equal columns */
grid-template-columns: repeat(auto-fit, minmax(200px, 1fr)); /* Responsive */
```

### Grid Item Placement

```css
.item {
  grid-column: span 2;      /* Span across 2 columns */
  grid-row: span 2;         /* Span across 2 rows */
  grid-column: 1 / 3;       /* From line 1 to line 3 */
}
```

---

## 🖼️ Backgrounds

```css
background-color: #eeeeee;
background-image: url("bg.jpg");
background-size: cover;       /* cover | contain | auto | px */
background-position: center;  /* center | top | bottom | left | right */
background-repeat: no-repeat; /* no-repeat | repeat | repeat-x | repeat-y */
background-attachment: fixed; /* Parallax-like effect */
```

### Shorthand

```css
background: #eee url("bg.jpg") no-repeat center / cover;
```

### Gradients

```css
/* Linear gradient */
background: linear-gradient(to right, red, blue);
background: linear-gradient(135deg, #667eea, #764ba2);

/* Radial gradient */
background: radial-gradient(circle, red, blue);
```

---

## ✨ Effects & Shadows

### Box Shadow

```css
box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);

/* Multiple shadows */
box-shadow: 0 2px 5px rgba(0,0,0,0.1), 0 8px 20px rgba(0,0,0,0.15);
```

### Text Shadow

```css
text-shadow: 2px 2px 5px gray;
```

### Border Radius

```css
border-radius: 10px;     /* All corners */
border-radius: 50%;      /* Circle / pill shape */
border-radius: 10px 0;   /* Top-left/bottom-right, top-right/bottom-left */
```

### Opacity & Filter

```css
opacity: 0.8;

filter: blur(4px);
filter: brightness(1.2);
filter: grayscale(100%);
```

---

## 🎞️ Transitions & Animations

### Transitions

Smoothly animate a property change between states.

```css
button {
  background: blue;
  transition: background 0.3s ease;
}

button:hover {
  background: red;
}
```

```css
/* Transition multiple properties */
transition: background 0.3s ease, transform 0.2s ease;

/* Transition all properties */
transition: all 0.3s ease;
```

### Animations with `@keyframes`

```css
@keyframes slide {
  from { transform: translateX(0); }
  to   { transform: translateX(200px); }
}

.box {
  animation: slide 2s ease-in-out infinite;
}
```

### Multi-Step Keyframes

```css
@keyframes bounce {
  0%   { transform: translateY(0); }
  50%  { transform: translateY(-30px); }
  100% { transform: translateY(0); }
}
```

### Animation Properties

```css
animation-name: slide;
animation-duration: 2s;
animation-timing-function: ease-in-out;
animation-delay: 0.5s;
animation-iteration-count: infinite;  /* or a number */
animation-direction: alternate;
animation-fill-mode: forwards;
```

---

## 📱 Responsive Design

### Media Queries

Apply styles based on screen size or device.

```css
@media (max-width: 768px) {
  body { background: red; }
}

@media (min-width: 768px) and (max-width: 1200px) {
  .container { width: 90%; }
}
```

### Common Breakpoints

| Breakpoint | Screen Size |
|------------|-------------|
| `480px` | Mobile (small) |
| `768px` | Tablet |
| `1024px` | Laptop |
| `1200px` | Desktop |

### 📱 Mobile-First Approach ✅ Recommended

Start with styles for small screens, then scale up.

```css
/* Base: mobile styles */
.container { width: 100%; }

/* Tablet and up */
@media (min-width: 768px) {
  .container { width: 80%; }
}

/* Desktop and up */
@media (min-width: 1200px) {
  .container { width: 70%; }
}
```

---

## ⚙️ Variables & Functions

### CSS Variables (Custom Properties)

Defined in `:root` to be available globally.

```css
:root {
  --main-color: #3498db;
  --font-size-base: 16px;
  --spacing-md: 20px;
}

h1 {
  color: var(--main-color);
}

p {
  font-size: var(--font-size-base);
  margin: var(--spacing-md);
}
```

### Useful CSS Functions

```css
/* calc() — math with mixed units */
width: calc(100% - 50px);
height: calc(100vh - 60px);

/* clamp() — fluid sizing with min/max bounds */
font-size: clamp(16px, 2vw, 24px);
/* min value, preferred value, max value */

/* min() and max() */
width: min(500px, 100%);
width: max(300px, 50%);
```

---

## 🧠 Best Practices

### ✅ Do This

- Use **external CSS files** to keep styles separate from HTML
- Use **classes** over IDs for styling (IDs have high specificity)
- Use **Flexbox or Grid** for layout instead of floats or tables
- Follow a **mobile-first** approach for responsive design
- Use **CSS variables** for colors, spacing, and font sizes
- Use **`box-sizing: border-box`** globally
- Keep selectors **short and specific**
- **Group related styles** together and add comments for sections

### ❌ Avoid This

- Inline CSS (hard to maintain and override)
- Overusing `!important` (breaks the cascade)
- Fixed widths everywhere (breaks responsiveness)
- Deeply nested selectors (slow and hard to read)
- Using only IDs for styling (too high specificity)

---

> ✨ **End of CSS Notes** — You now have a complete HTML + CSS reference!
