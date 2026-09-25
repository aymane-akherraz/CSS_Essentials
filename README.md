# CSS Essentials

*CSS (Cascading Style Sheets) is a language used to style and format the presentation of HTML elements in web pages.*

CSS defines the rules that control how elements **look, behave, and are positioned** on a webpage.

---

## Table of Contents

* [Introduction](#introduction)
* [How to Add CSS to Web Pages](#how-to-add-css-to-web-pages)

  * [Inline Styles](#inline-styles)
  * [Internal Styles](#internal-styles)
  * [External Stylesheets](#external-stylesheets)
  * [Comparison](#comparison)
* [CSS Rules](#css-rules)

  * [Combining Selectors](#combining-selectors)
  * [Multiple Property Values](#multiple-property-values)
* [Comments](#comments)
* [CSS Selectors](#css-selectors)

  * [Element Selectors](#element-selectors)
  * [Class Selectors](#class-selectors)
  * [ID Selectors](#id-selectors)
  * [Attribute Selectors](#attribute-selectors)
  * [Pseudo-Classes](#pseudo-classes)
  * [Pseudo-Elements](#pseudo-elements)
  * [Combinators](#combinators)
* [The CSS Cascade](#the-css-cascade)

  * [Specificity](#specificity)
  * [Inheritance](#inheritance)
  * [Overriding Inherited Properties](#overriding-inherited-properties)
  * [`!important`](#important)
* [Best Practices](#best-practices)
* [License](#license)

---

## Introduction

CSS stands for **Cascading Style Sheets**.

It is used to control the **appearance and layout** of HTML elements. While HTML provides the structure of a webpage, CSS controls things such as:

* Colors
* Fonts
* Sizes
* Spacing
* Positioning
* Layout
* Visual effects

---

# How to Add CSS to Web Pages

There are three main ways to add CSS to an HTML document:

1. **Inline styles**
2. **Internal styles**
3. **External stylesheets**

---

## Inline Styles

Inline CSS is written directly inside an HTML element using the `style` attribute.

It is useful for **quick, specific changes**, but can make HTML harder to maintain when used extensively.

```html
<p style="color: blue;">Hello, CSS!</p>
```

---

## Internal Styles

Internal CSS is written inside a `<style>` element, usually within the `<head>` of an HTML document.

It is useful when the styles are only needed for a **single page**.

```html
<head>
  <style>
    p {
      color: red;
    }
  </style>
</head>

<body>
  <p>Hello, CSS!</p>
</body>
```

---

## External Stylesheets

External CSS is stored in a separate `.css` file and linked to the HTML document.

This is generally the preferred approach for **larger projects and multiple pages** because it keeps structure and styling separate.

### `index.html`

```html
<head>
  <link rel="stylesheet" href="styles.css">
</head>

<body>
  <p>Hello, CSS!</p>
</body>
```

### `styles.css`

```css
p {
  color: green;
}
```

---

## Comparison

| Method       | Advantages                                 | Disadvantages                             |
| ------------ | ------------------------------------------ | ----------------------------------------- |
| **Inline**   | Quick and simple; affects one element      | Hard to maintain; mixes HTML and CSS      |
| **Internal** | Keeps styles together; useful for one page | Not easily reusable across multiple pages |
| **External** | Reusable, organized, and maintainable      | Requires a separate file and link         |

---

# CSS Rules

A **CSS rule** defines how one or more HTML elements should be styled.

A rule consists of:

* A **selector** — identifies the elements to style.
* **Properties** — define what aspect of the element is changed.
* **Values** — define how the property should be changed.

### Basic Syntax

```css
selector {
  property: value;
  another-property: another-value;
}
```

### Example

```css
h1 {
  font-size: 24px;
  color: green;
}

p {
  font-size: 16px;
  color: blue;
}
```

Here:

* `h1` and `p` are **selectors**.
* `font-size` and `color` are **properties**.
* `24px`, `16px`, `green`, and `blue` are **values**.

---

## Combining Selectors

Multiple selectors can be combined using commas when they need the same styles.

```css
h1, p {
  font-size: 18px;
  color: blue;
}
```

This applies the same styles to both `<h1>` and `<p>` elements.

Combining selectors helps keep CSS **shorter and easier to maintain**.

---

## Multiple Property Values

Some CSS properties accept multiple values.

A common example is `font-family`, where fonts can be provided as fallbacks:

```css
p {
  font-family: "Roboto", Arial, sans-serif;
}
```

The browser tries the fonts from left to right:

1. `Roboto`
2. `Arial`
3. Generic `sans-serif`

If the first font is unavailable, the browser tries the next one.

---

# Comments

CSS comments are written between `/*` and `*/`.

Comments are ignored by the browser and do not affect styling.

### Single-Line Comment

```css
/* This is a comment */

selector {
  property: value; /* Another comment */
}
```

### Multi-Line Comment

```css
/*
  This is a multi-line comment.
  It can span multiple lines.
*/
```

Comments are useful for **explaining code and organizing stylesheets**.

---

# CSS Selectors

CSS selectors determine **which HTML elements receive a style**.

The main selectors covered here are:

* Element selectors
* Class selectors
* ID selectors
* Attribute selectors
* Pseudo-classes
* Pseudo-elements
* Combinators

---

## Element Selectors

An element selector targets all elements with a specific HTML tag.

```css
p {
  color: red;
}
```

This targets every `<p>` element on the page.

---

## Class Selectors

A class selector targets elements with a specific `class` attribute.

It starts with a `.` followed by the class name.

```css
.button {
  background-color: blue;
  color: white;
}
```

HTML:

```html
<button class="button">Click Me</button>
```

Classes are useful when the same style needs to be applied to **multiple elements**.

---

## ID Selectors

An ID selector targets an element with a specific `id`.

It starts with `#` followed by the ID name.

```css
#header {
  font-size: 24px;
  color: green;
}
```

HTML:

```html
<div id="header">
  Welcome
</div>
```

An ID should identify a **unique element** on a page.

### Class vs ID

| Selector | Syntax    | Typical Use               |
| -------- | --------- | ------------------------- |
| Element  | `p`       | All elements of a type    |
| Class    | `.button` | Styling multiple elements |
| ID       | `#header` | A unique element          |

As a general practice, **use classes for styling** and reserve IDs mainly for unique elements or functionality.

IDs also have **higher specificity** than classes.

---

# Attribute Selectors

Attribute selectors target elements based on their HTML attributes.

For example:

```html
<p>
  Numbers:
  <span data-highlight>123</span>
  <span data-highlight>456</span>
</p>
```

```css
[data-highlight] {
  background-color: yellow;
}
```

This targets every element containing the `data-highlight` attribute.

---

## Exact Match Selector

Targets elements whose attribute exactly matches a value.

```css
[attribute="value"] {
  /* styles */
}
```

Example:

```css
[data-highlight="true"] {
  background-color: yellow;
}
```

---

## Substring Match Selector

Targets elements whose attribute contains a specific value.

```css
[attribute*="value"] {
  /* styles */
}
```

Example:

```css
[class*="button"] {
  border: 1px solid black;
}
```

---

## Prefix Match Selector

Targets elements whose attribute starts with a specific value.

```css
[attribute^="value"] {
  /* styles */
}
```

Example:

```css
[href^="https://"] {
  color: blue;
}
```

---

## Suffix Match Selector

Targets elements whose attribute ends with a specific value.

```css
[attribute$="value"] {
  /* styles */
}
```

Example:

```css
[src$=".png"] {
  border: 1px solid black;
}
```

Attribute selectors are useful when you want to style elements **without adding additional classes or IDs**.

---

# Pseudo-Classes, Pseudo-Elements, and Combinators

CSS also provides specialized selectors for states, parts of elements, and relationships between elements.

---

## Pseudo-Classes

Pseudo-classes target elements based on their **state or user interaction**.

Examples:

```css
button:hover {
  background-color: blue;
}

input:focus {
  border-color: green;
}
```

* `:hover` — when the user moves the pointer over an element.
* `:focus` — when an element receives focus.

---

## Pseudo-Elements

Pseudo-elements target **specific parts of an element**.

Common examples include:

```css
.element::before {
  content: "→ ";
}

.element::after {
  content: " ✓";
}
```

Common pseudo-elements include:

* `::before`
* `::after`

---

## Combinators

Combinators select elements based on their relationship with other elements.

### Descendant

A space selects elements **inside another element**.

```css
div p {
  color: blue;
}
```

Targets `<p>` elements anywhere inside a `<div>`.

### Child

`>` selects **direct children**.

```css
div > p {
  color: red;
}
```

### Adjacent Sibling

`+` selects an element that **immediately follows another element**.

```css
h1 + p {
  color: green;
}
```

---

# The CSS Cascade

The **CSS cascade** determines which style is applied when multiple CSS rules affect the same element.

The browser considers factors such as:

* The source of the style
* Specificity
* The order of declarations
* Browser defaults

When rules conflict, the browser determines which declaration has precedence.

---

## Specificity

**Specificity** describes how specifically a selector targets an element.

A simplified order is:

```text
ID
 ↓
Class / Attribute / Pseudo-class
 ↓
Element / Pseudo-element
```

For example:

```css
.header {
  color: blue;
}

#header {
  color: red;
}
```

If both rules apply to the same element, the ID selector has higher specificity.

> The more specific selector generally takes precedence when declarations conflict.

---

# Inheritance

**Inheritance** allows certain CSS properties applied to a parent element to be passed to its children.

For example:

```css
.parent {
  font-family: Arial, sans-serif;
  font-size: 16px;
  border: 1px solid black;
  padding: 10px;
}
```

```html
<div class="parent">
  <p>This is a child paragraph.</p>
</div>
```

The `<p>` inherits properties such as:

* `font-family`
* `font-size`

However, properties such as `border`, `padding`, `width`, and `height` are generally **not inherited automatically**.

---

## Overriding Inherited Properties

Inherited styles can be overridden by applying a style directly to the child element.

```css
.parent {
  font-family: Arial, sans-serif;
  font-size: 16px;
}

p {
  font-size: 20px;
  color: green;
}
```

```html
<div class="parent">
  <p>This is a child paragraph.</p>
</div>
```

The `<p>` inherits the parent's font family but uses its own `font-size` and `color` declarations.

---

# `!important`

The `!important` declaration gives a CSS declaration higher precedence than normal declarations.

```css
.heading {
  color: blue !important;
}
```

This can override declarations that would normally win through specificity or source order.

However, excessive use of `!important` can make CSS **harder to maintain and debug**.

---

## When to Use `!important`

There are situations where `!important` can be useful, such as:

* Overriding browser default styles
* Overriding third-party CSS
* Resolving difficult specificity conflicts
* Applying a temporary critical fix

It should generally be treated as a **last resort**.

---

# Best Practices

### 1. Use `!important` Sparingly

Only use it when there is a clear reason and other approaches are not practical.

### 2. Keep Specificity Under Control

Prefer simple, well-structured selectors instead of deeply nested or overly specific selectors.

### 3. Use Classes for Styling

Classes are reusable and generally easier to maintain than IDs for styling.

### 4. Keep CSS Organized

For larger projects, prefer external stylesheets and organize related styles logically.

### 5. Document Important Overrides

If `!important` is necessary, add a comment explaining why.

```css
/* Required to override third-party library styles */
.button {
  color: white !important;
}
```

---

# License

The content in this repository is based on the **CSS Essentials** course from **Cisco Networking Academy (NetAcad)**.

This repository is intended for **educational and learning purposes**. The original course material and concepts remain the property of their respective copyright holders.

No ownership of the original NetAcad course material is claimed.
