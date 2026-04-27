# 🌐 HTML Complete Reference Notes

A structured documentation of HTML concepts — from basics to advanced topics.


---

## Table of Contents

- [🏗️ Basic Structure](#️-basic-structure)
- [💬 Comments](#-comments)
- [🔤 Text & Formatting](#-text--formatting)
- [🔗 Links & Navigation](#-links--navigation)
- [🖼️ Images & Media](#️-images--media)
- [📋 Lists](#-lists)
- [📊 Tables](#-tables)
- [📝 Forms](#-forms)
- [🧠 Semantic HTML](#-semantic-html)
- [⚙️ HTML Attributes](#️-html-attributes)
- [🔣 Entities & Symbols](#-entities--symbols)
- [♿ Accessibility (A11Y)](#-accessibility-a11y)
- [🔎 SEO Basics](#-seo-basics)
- [📱 Responsive HTML](#-responsive-html)
- [🚀 Advanced Concepts](#-advanced-concepts)
- [⚡ HTML APIs](#-html-apis)

---

## 🏗️ Basic Structure

Every HTML page follows a standard boilerplate structure.

### 📄 Standard HTML Template
```html
<!DOCTYPE html>
<html>
  <head>
    <title>My Page</title>
  </head>
  <body>
    Content goes here
  </body>
</html>
```
### 🏷️ Important Tags

| Tag | Purpose |
|-----|---------|
| `<!DOCTYPE html>` | Declares HTML5 document |
| `<html>` | Root element of the page |
| `<head>` | Contains metadata (not visible) |
| `<title>` | Text shown in the browser tab |
| `<body>` | Visible content of the webpage |

---

## 💬 Comments

Comments help developers understand code and are *ignored by browsers*.

<!-- This is a comment -->

---

## 🔤 Text & Formatting

### 🔠 Headings

Used to define titles and subtitles. Ranges from <h1> (largest) to <h6> (smallest).

<h1>Main Heading</h1>
<h2>Sub Heading</h2>
<h3>Section Heading</h3>
<h6>Smallest Heading</h6>

### 📄 Paragraph

Used for blocks of text.

<p>This is a paragraph.</p>

### ↩️ Line Break & Divider

<br>   <!-- Line break (inline) -->
<hr>   <!-- Horizontal rule / divider -->

### ✍️ Text Formatting Tags

<b>Bold</b>
<i>Italic</i>
<u>Underline</u>
<strong>Important</strong>
<em>Emphasis</em>

**`<strong>` vs `<em>`**
- `<strong>` → Indicates **importance** (semantic weight)
- `<em>` → Indicates *emphasis* (semantic stress)


### 🔬 Superscript & Subscript

x<sup>2</sup>    <!-- x² -->
H<sub>2</sub>O   <!-- H₂O -->

### 💬 Quotes & Code

<blockquote>This is a quoted block.</blockquote>
<code>print("Hello World")</code>

---

## 🔗 Links & Navigation

### 🔗 Basic Anchor Tag

<a href="https://example.com">Visit Site</a>

### 🌐 Internal vs External Links

<!-- Internal (same site) -->
<a href="about.html">About Page</a>

<!-- External (different site) -->
<a href="https://google.com">Google</a>

### 🆕 Open Link in New Tab

<a href="https://google.com" target="_blank">Open in New Tab</a>

### 📧 Email & Phone Links

<a href="mailto:test@email.com">Send Email</a>
<a href="tel:+880123456">Call Us</a>

### 🔖 Bookmark / Same-Page Links

Jump to a specific section within the same page.

<!-- The link -->
<a href="#section1">Go to Section</a>

<!-- The target -->
<h2 id="section1">Section Title</h2>

---

## 🖼️ Images & Media

### 🖼️ Image Tag

<img src="image.jpg" alt="A description of the image">

| Attribute | Purpose |
|-----------|---------|
| src | Path to the image file |
| alt | Accessibility description |
| width | Sets the image width |
| height | Sets the image height |

### 🔊 Audio

<audio controls>
  <source src="song.mp3">
</audio>

### 🎬 Video

<video controls width="400">
  <source src="video.mp4">
</video>

### ▶️ YouTube Embed (iframe)

<iframe src="https://www.youtube.com/embed/VIDEOID"></iframe>

### 🖼️ Figure & Caption

<figure>
  <img src="img.jpg" alt="Description">
  <figcaption>This is the image caption.</figcaption>
</figure>

---

## 📋 Lists

### 🔢 Ordered List

Items are numbered automatically.

<ol>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</ol>

### 🔘 Unordered List

Items are displayed with bullet points.

<ul>
  <li>Item one</li>
  <li>Item two</li>
  <li>Item three</li>
</ul>

### 📖 Description List

Used for term-definition pairs.

<dl>
  <dt>HTML</dt>
  <dd>A markup language for creating web pages.</dd>

  <dt>CSS</dt>
  <dd>A stylesheet language for styling web pages.</dd>
</dl>

### 🧩 Nested Lists

Lists can be placed inside other list items.

<ul>
  <li>Fruits
    <ul>
      <li>Apple</li>
      <li>Banana</li>
    </ul>
  </li>
</ul>

---

## 📊 Tables

### 📊 Basic Table Structure

<table>
  <tr>
    <th>Name</th>
    <th>Age</th>
  </tr>
  <tr>
    <td>Tanjiro</td>
    <td>15</td>
  </tr>
</table>

### 🧱 Table Sections

<table>
  <thead>  <!-- Table header -->
    <tr><th>Column</th></tr>
  </thead>
  <tbody>  <!-- Table body -->
    <tr><td>Data</td></tr>
  </tbody>
  <tfoot>  <!-- Table footer -->
    <tr><td>Summary</td></tr>
  </tfoot>
</table>

### 🔗 Merge Cells

<!-- Span across 2 columns -->
<td colspan="2">Merged Column</td>

<!-- Span across 2 rows -->
<td rowspan="2">Merged Row</td>

---

## 📝 Forms

⚠️ Forms are one of the most important parts of HTML for user interaction.


### 📝 Basic Form

<form action="/submit" method="POST">
  <input type="text" name="username">
</form>

### ⌨️ Common Input Types

<input type="text">       <!-- Plain text -->
<input type="email">      <!-- Email address -->
<input type="password">   <!-- Hidden text -->
<input type="number">     <!-- Numeric value -->
<input type="date">       <!-- Date picker -->
<input type="file">       <!-- File upload -->

### 🏷️ Labels

Labels improve accessibility by associating text with inputs.

<label for="name">Full Name:</label>
<input type="text" id="name">

### 🔘 Buttons

<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Click Me</button>

### 📄 Textarea

Multi-line text input.

<textarea rows="4" cols="50">Enter your message here...</textarea>

### 🔽 Select Dropdown

<select name="city">
  <option value="dhaka">Dhaka</option>
  <option value="chittagong">Chittagong</option>
</select>

### ☑️ Radio & Checkbox

<!-- Radio (select one) -->
<input type="radio" name="gender" value="male"> Male
<input type="radio" name="gender" value="female"> Female

<!-- Checkbox (select multiple) -->
<input type="checkbox" name="html"> HTML
<input type="checkbox" name="css"> CSS

### ✅ Basic Validation

<input type="text" required>           <!-- Field must be filled -->
<input type="email">                   <!-- Must be valid email format -->
<input type="number" min="1" max="10"> <!-- Number range -->
<input type="text" maxlength="50">     <!-- Max character limit -->

---

## 🧠 Semantic HTML

Semantic tags clearly describe their meaning to both the browser and the developer.

### 🏗️ Semantic Layout Tags

<header>   <!-- Page/section header -->
<nav>      <!-- Navigation links -->
<main>     <!-- Main content area -->
<section>  <!-- Grouped section of content -->
<article>  <!-- Standalone piece of content -->
<aside>    <!-- Sidebar / supplementary content -->
<footer>   <!-- Page/section footer -->

### ✅ Why Semantic HTML Matters

| Benefit | Explanation |
|---------|-------------|
| 🔎 Better SEO | Search engines understand the content structure |
| ♿ Accessibility | Screen readers navigate the page more easily |
| 🧹 Cleaner Code | Code is more readable and meaningful |

---

## ⚙️ HTML Attributes

### 🏷️ Common Attributes

| Attribute | Purpose |
|-----------|---------|
| id | Unique identifier for an element |
| class | Groups elements for CSS/JS targeting |
| style | Inline CSS styling |
| title | Tooltip text on hover |
| alt | Alternative text for images |
|data-*` | Custom data attributes |
💡 **Global attributes** work on **all** HTML elements.
.

<p id="intro" class="text-gray" title="Introduction paragraph">
  Hello World
</p>

<!-- Custom data attribute -->
<div data-user-id="42">Profile</div>

---

## 🔣 Entities & Symbols

Used to display reserved or special characters in HTML.

### Reserved Characters

| Code | Renders As |
|------|-----------|
| &lt; | < |
| &gt; | > |
| &amp; | & |
| &nbsp; | (non-breaking space) |
|&copy;` | © |
|&reg;` | ® |

### 😀 Emojis via Entity Code
&#128512;   <!-- 😀 -->
&#10084;    <!-- ❤️ -->


---

## ♿ Accessibility (A11Y)

Making your HTML usable for everyone, including people using screen readers.

### ✅ Key Practices

- Always use alt attributes on images
- Use semantic tags instead of generic <div> and <span>
- Always associate <label> with form inputs
- Maintain a proper heading order (h1 → h2 → h3)
- Use ARIA roles when semantic HTML isn't enough

<!-- Good: labelled input -->
<label for="email">Email Address:</label>
<input type="email" id="email" aria-required="true">

<!-- Good: image with alt text -->
<img src="logo.png" alt="Company Logo">

<!-- Good: button with descriptive label -->
<button aria-label="Close menu">✕</button>

---

## 🔎 SEO Basics

### 🏷️ Essential Meta Tags

<head>
  <meta charset="UTF-8">
  <meta name="description" content="A brief description of your page.">
  <meta name="keywords" content="html, web, tutorial">
  <meta name="author" content="Your Name">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>

### ⭐ Favicon

<link rel="icon" href="favicon.ico" type="image/x-icon">

### 📱 Open Graph (Social Media Previews)

Used to control how your page appears when shared on social media.

<meta property="og:title" content="Page Title">
<meta property="og:description" content="Page description here.">
<meta property="og:image" content="https://example.com/preview.jpg">
<meta property="og:url" content="https://example.com">

---

## 📱 Responsive HTML

### 📐 Viewport Meta Tag

Always include this to make pages mobile-friendly.

<meta name="viewport" content="width=device-width, initial-scale=1.0">

### 🖼️ Responsive Images

<!-- Simple max-width approach -->
<img src="img.jpg" alt="Description" style="max-width: 100%;">

<!-- Srcset for different screen sizes -->
<img
  src="img-small.jpg"
  srcset="img-medium.jpg 768w, img-large.jpg 1200w"
  alt="Responsive image"
>

---

## 🚀 Advanced Concepts

### 🪟 iframe (Inline Frame)

Embeds another HTML page or external content inside your page.

<iframe src="page.html" width="600" height="400"></iframe>

<!-- YouTube embed -->
<iframe
  src="https://www.youtube.com/embed/VIDEOID"
  allowfullscreen>
</iframe>

### 🎨 Canvas

Used to draw graphics and animations via JavaScript.

<canvas id="myCanvas" width="500" height="300"></canvas>

### 🎨 SVG (Scalable Vector Graphics)

Used to render vector-based graphics directly in HTML.

<svg width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="blue" />
</svg>

### 🔽 Details & Summary (Accordion)

Creates a native expandable/collapsible element.

<details>
  <summary>Click to expand</summary>
  <p>This hidden content appears when expanded.</p>
</details>

### 📈 Progress & Meter

<!-- Progress bar -->
<progress value="70" max="100"></progress>

<!-- Meter (gauge) -->
<meter value="0.7" min="0" max="1">70%</meter>

---

## ⚡ HTML APIs

Built-in browser APIs accessible through HTML and JavaScript.

| API | Use Case |
|-----|----------|
| *Geolocation API* | Get user's current location |
| *Drag & Drop API* | Drag elements across the page |
| *Web Storage API* | Store data in localStorage / sessionStorage |
| *Canvas API* | Draw 2D graphics and animations |
| *Fullscreen API* | Display elements in fullscreen mode |
| *Notification API* | Show browser push notifications |

---

✨ **End of HTML Notes** — Happy coding!
