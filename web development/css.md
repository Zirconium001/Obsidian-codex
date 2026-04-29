# 🎨 CSS Complete Reference

> A structured, professional reference for CSS — from fundamentals to advanced topics.

---

## 📋 Table of Contents

| # | Topic |
|---|-------|
| 1 | [What is CSS](#-what-is-css) |
| 2 | [CSS Syntax](#-css-syntax) |
| 3 | [Selectors](#-selectors) |
| 4 | [Colors & Units](#-colors--units) |
| 5 | [Typography](#-typography) |
| 6 | [Box Model](#-box-model) |
| 7 | [Layout & Display](#-layout--display) |
| 8 | [Positioning](#-positioning) |
| 9 | [Flexbox](#-flexbox) |
| 10 | [CSS Grid](#-css-grid) |
| 11 | [Backgrounds](#-backgrounds) |
| 12 | [Effects & Shadows](#-effects--shadows) |
| 13 | [Transitions & Animations](#-transitions--animations) |
| 14 | [Responsive Design](#-responsive-design) |
| 15 | [Variables & Functions](#-variables--functions) |
| 16 | [Best Practices](#-best-practices) |

---

## 🎯 What is CSS

*CSS (Cascading Style Sheets)* controls the visual presentation of HTML elements.

| Layer | Technology | Role |
|-------|-----------|------|
| Structure | HTML | Content & markup |
| Style | CSS | Visual presentation |
| Behavior | JavaScript | Interactivity |

### Ways to Add CSS

*1. Inline CSS* — Applied directly to an element via the style attribute.

html
<p style="color: red;">Hello, World!</p>


> ⚠️ Avoid for anything beyond quick prototyping — it is hard to maintain.

---

*2. Internal CSS* — Defined inside a <style> tag within the <head>.

html
<style>
  p {
    color: red;
  }
</style>


> ⚠️ Suitable for single-page styles, but not scalable.

---

*3. External CSS* ✅ (Recommended)

html
<link rel="stylesheet" href="style.css">


> ✅ Keeps styles separate, reusable, and maintainable.

---

## 🧩 CSS Syntax

css
selector {
  property: value;
}


*Example:*

css
h1 {
  color: blue;
  font-size: 30px;
}


| Part | Description |
|------|-------------|
| selector | Targets the HTML element(s) to style |
| property | The style attribute to change |
| value | The value assigned to that property |

---

## 🎯 Selectors

### Basic Selectors

css
p       { }   /* Element selector   */
#title  { }   /* ID selector        */
.box    { }   /* Class selector     */
*       { }   /* Universal selector */


### Grouping Selector

css
h1, h2, h3 {
  color: blue;
}


### Combinator Selectors

css
/* Descendant — any <p> inside a <div> */
div p { color: red; }

/* Child — direct <p> children of <div> only */
div > p { color: green; }

/* Adjacent sibling */
h1 + p { color: gray; }

/* General sibling */
h1 ~ p { color: lightgray; }


### Attribute Selector

css
input[type="text"] {
  border: 1px solid black;
}


### Pseudo-Classes

css
a:hover         { color: red; }
button:active   { transform: scale(0.9); }
li:first-child  { color: blue; }
li:last-child   { color: green; }
li:nth-child(2) { color: orange; }


### Pseudo-Elements

css
p::first-letter { font-size: 30px; }
p::first-line   { font-weight: bold; }
p::before       { content: "★ "; }
p::after        { content: " ✓"; }


---

## 🎨 Colors & Units

### Color Formats

css
color: red;                   /* Named color     */
color: #ff0000;               /* Hex             */
color: rgb(255, 0, 0);        /* RGB             */
color: rgba(255, 0, 0, 0.5);  /* RGB + Alpha     */
color: hsl(0, 100%, 50%);     /* HSL             */
color: hsla(0, 100%, 50%, .5);/* HSL + Alpha     */


### Units

| Type | Examples | Use Case |
|------|----------|----------|
| Absolute | px, cm, mm | Fixed-size elements |
| Relative | %, em, rem | Scalable, accessible sizing |
| Viewport | vw, vh, vmin, vmax | Full-screen layouts |

css
font-size: 1.125rem;   /* Relative to root font size     */
width: 50%;            /* Relative to parent container   */
height: 100vh;         /* Full viewport height           */
padding: 2em;          /* Relative to element font size  */


> ✅ *Tip:* Prefer rem for font sizes and % or vw/vh for layout dimensions to ensure responsiveness.

---

## 🔤 Typography

css
font-family: "Georgia", serif;
font-size: 18px;
font-weight: 700;          /* bold */
font-style: italic;
line-height: 1.6;
text-align: center;
text-decoration: underline;
text-transform: uppercase;
letter-spacing: 0.05em;
word-spacing: 4px;


### Google Fonts Integration

html
<!-- In <head> -->
<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@400;600&display=swap" rel="stylesheet">


css
body {
  font-family: "Poppins", sans-serif;
}


---

## 📦 Box Model

Every HTML element is rendered as a rectangular box composed of four layers:


┌─────────────────────────────────┐
│            MARGIN               │
│  ┌───────────────────────────┐  │
│  │         BORDER            │  │
│  │  ┌─────────────────────┐  │  │
│  │  │       PADDING       │  │  │
│  │  │  ┌───────────────┐  │  │  │
│  │  │  │    CONTENT    │  │  │  │
│  │  │  └───────────────┘  │  │  │
│  │  └─────────────────────┘  │  │
│  └───────────────────────────┘  │
└─────────────────────────────────┘


css
div {
  width: 200px;
  padding: 20px;
  border: 5px solid black;
  margin: 10px;
}


### Box Sizing

By default, width does not include padding or border. Use border-box to include them:

css
/* Apply globally — recommended */
*,
*::before,
*::after {
  box-sizing: border-box;
}


| Value | Behavior |
|-------|----------|
| content-box | Default. width = content only |
| border-box | width includes padding + border |

---

## 📐 Layout & Display

css
display: block;        /* Stacks vertically, full width         */
display: inline;       /* Flows with text, no width/height      */
display: inline-block; /* Inline flow with block sizing support */
display: flex;         /* Flexbox container                     */
display: grid;         /* Grid container                        */
display: none;         /* Removes element from layout           */


### Visibility vs Display

css
visibility: hidden;  /* Element is invisible but still occupies space */
display: none;       /* Element is removed entirely from the layout   */


---

## 📏 Positioning

css
position: static;    /* Default — normal document flow            */
position: relative;  /* Offset from its normal position           */
position: absolute;  /* Positioned relative to nearest positioned ancestor */
position: fixed;     /* Fixed relative to the viewport            */
position: sticky;    /* Sticks at a scroll threshold              */


css
.box {
  position: absolute;
  top: 20px;
  right: 0;
  bottom: 0;
  left: 50px;
}


### Z-Index (Stacking Order)

css
.modal {
  position: absolute;
  z-index: 100;
}


> ✅ z-index only works on elements with a position value other than static.

---

## 🧱 Flexbox

Flexbox is a *one-dimensional* layout system for arranging items in a row or column.

css
.container {
  display: flex;
}


### Container Properties

css
.container {
  flex-direction: row;           /* row | column | row-reverse | column-reverse */
  justify-content: center;       /* Alignment along main axis   */
  align-items: center;           /* Alignment along cross axis  */
  flex-wrap: wrap;               /* Allow items to wrap         */
  gap: 20px;                     /* Space between items         */
}


### Item Properties

css
.item {
  flex: 1;            /* Grow to fill available space      */
  flex-shrink: 0;     /* Prevent item from shrinking       */
  align-self: center; /* Override container's align-items  */
  order: 2;           /* Change visual order               */
}


### Perfect Centering

css
.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}


---

## 🧮 CSS Grid

CSS Grid is a *two-dimensional* layout system for rows and columns.

css
.container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;  /* 3 equal columns */
  grid-template-rows: auto;
  gap: 20px;
}


### Useful Shorthands

css
/* Repeat 3 equal columns */
grid-template-columns: repeat(3, 1fr);

/* Auto-fill responsive columns */
grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));


### Item Placement

css
.item {
  grid-column: span 2;    /* Span across 2 columns */
  grid-row: span 1;       /* Span across 1 row     */
  grid-column: 1 / 3;     /* From line 1 to line 3 */
}


> ✅ *Rule of thumb:* Use *Flexbox* for components (navbars, cards) and *Grid* for page-level layouts.

---

## 🖼️ Backgrounds

css
background-color: #eeeeee;
background-image: url("bg.jpg");
background-size: cover;        /* cover | contain | auto */
background-position: center;
background-repeat: no-repeat;
background-attachment: fixed;  /* Parallax effect        */


### Shorthand

css
background: #eee url("bg.jpg") no-repeat center / cover;


### Gradients

css
/* Linear gradient */
background: linear-gradient(to right, #ff0000, #0000ff);

/* Radial gradient */
background: radial-gradient(circle, #ff0000, #0000ff);

/* Multi-stop gradient */
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);


---

## ✨ Effects & Shadows

css
/* Box shadow */
box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);

/* Multiple shadows */
box-shadow: 0 2px 4px rgba(0,0,0,.1), 0 8px 16px rgba(0,0,0,.15);

/* Text shadow */
text-shadow: 2px 2px 5px rgba(0, 0, 0, 0.3);

/* Rounded corners */
border-radius: 10px;
border-radius: 50%;    /* Circle */

/* Transparency */
opacity: 0.8;

/* CSS filter effects */
filter: blur(4px);
filter: grayscale(100%);
filter: drop-shadow(0 4px 6px rgba(0,0,0,.1));


---

## 🎞️ Transitions & Animations

### Transitions

Smoothly animate a property change between two states.

css
button {
  background: blue;
  transition: background 0.3s ease, transform 0.2s ease;
}

button:hover {
  background: red;
  transform: translateY(-2px);
}


| Property | Description |
|----------|-------------|
| transition-property | Which property to animate |
| transition-duration | How long the transition takes |
| transition-timing-function | Easing (ease, linear, ease-in-out) |
| transition-delay | Delay before the transition begins |

### Animations

Define multi-step animations with @keyframes.

css
@keyframes slideIn {
  from {
    transform: translateX(-100%);
    opacity: 0;
  }
  to {
    transform: translateX(0);
    opacity: 1;
  }
}

.box {
  animation: slideIn 0.5s ease forwards;
}


### Animation Properties

css
.box {
  animation-name: slideIn;
  animation-duration: 2s;
  animation-timing-function: ease-in-out;
  animation-delay: 0.5s;
  animation-iteration-count: infinite;  /* or a number */
  animation-direction: alternate;
  animation-fill-mode: forwards;
}


---

## 📱 Responsive Design

### Media Queries

Apply styles based on screen size or device characteristics.

css
/* Tablet and below */
@media (max-width: 768px) {
  body {
    font-size: 14px;
  }
}

/* Mobile only */
@media (max-width: 480px) {
  .container {
    flex-direction: column;
  }
}

/* Landscape orientation */
@media (orientation: landscape) {
  .hero {
    height: 50vh;
  }
}


### Common Breakpoints

| Name | Width |
|------|-------|
| Mobile | < 480px |
| Tablet | < 768px |
| Laptop | < 1024px |
| Desktop | < 1280px |
| Wide | ≥ 1280px |

### Mobile-First Approach ✅ (Recommended)

Start with styles for small screens, then scale up:

css
/* Base — mobile */
.container {
  width: 100%;
  padding: 1rem;
}

/* Tablet and above */
@media (min-width: 768px) {
  .container {
    width: 80%;
    padding: 2rem;
  }
}

/* Desktop and above */
@media (min-width: 1024px) {
  .container {
    width: 70%;
    max-width: 1200px;
    margin: 0 auto;
  }
}


---

## ⚙️ Variables & Functions

### CSS Custom Properties (Variables)

Define reusable values scoped to :root for global access.

css
:root {
  --color-primary: #3b82f6;
  --color-secondary: #10b981;
  --font-size-base: 1rem;
  --spacing-lg: 2rem;
  --border-radius: 8px;
}

h1 {
  color: var(--color-primary);
  font-size: calc(var(--font-size-base) * 2);
}

.card {
  border-radius: var(--border-radius);
  padding: var(--spacing-lg);
}


### Useful CSS Functions

css
/* Arithmetic */
width: calc(100% - 60px);

/* Responsive font sizing — min, preferred, max */
font-size: clamp(1rem, 2.5vw, 1.5rem);

/* Minimum of two values */
width: min(90%, 600px);

/* Maximum of two values */
width: max(300px, 50%);


---

## 🧠 Best Practices

### ✅ Do

- Use *external stylesheets* to separate concerns
- Prefer *classes* over IDs for styling (IDs have higher specificity and are harder to override)
- Use *box-sizing: border-box* globally
- Use *Flexbox and Grid* for layout instead of floats or absolute positioning
- Follow a *mobile-first* responsive strategy
- Use *CSS variables* for colors, spacing, and typography to ensure consistency
- Keep selectors *shallow and specific* — avoid over-nesting
- Group and *comment sections* in large stylesheets

### ❌ Avoid

| Anti-Pattern | Why |
|---|---|
| Inline style attributes | Not reusable, hard to maintain |
| Overusing !important | Breaks the cascade, causes debugging nightmares |
| Fixed widths on layout elements | Breaks on different screen sizes |
| Too-deep selector nesting | Increases specificity and reduces reusability |
| Styling with IDs | High specificity makes overriding difficult |
| Magic numbers without comments | Code becomes unreadable over time |

---

## 📚 Further Reading

- [MDN Web Docs — CSS](https://developer.mozilla.org/en-US/docs/Web/CSS)
- [CSS Tricks — A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
- [CSS Tricks — A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Can I Use](https://caniuse.com/) — Browser compatibility tables

---

<div align="center">
  <sub>Part of the Web Development Reference Series · HTML · <strong>CSS</strong> · JavaScript</sub>
</div>
