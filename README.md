# Perfect UI Corner Calculator

A lightweight, zero-dependency visual tool to calculate mathematically harmonious, concentric nested border radii for cards and containers. Built with semantic HTML, modern vanilla CSS, and vanilla JavaScript.

[Live Demo](https://trudymessingham.co.uk/playground/perfect-ui-corner-calculator/) • [Tutorials & Guides](https://trudymessingham.co.uk/tutorials/) • [Author Portfolio](https://trudymessingham.co.uk/portfolio/)

---

## The Problem: The Nested Corner Illusion

When nesting an element inside a rounded container with padding, applying the same `border-radius` to both elements creates an optical mismatch. The inner corner looks distorted, cramped, or disjointed because the curves do not share the same concentric centre point.

To achieve visual harmony, the inner radius must account for the parent container's padding:

$$\text{Inner Radius} = \max(0, \text{Outer Radius} - \text{Padding})$$

If the padding exceeds the outer radius, the inner corner should naturally resolve to a sharp right angle (`0px`) rather than an awkward curve.

---

## Features

- **Interactive Visual Preview:** Adjust outer radius, padding, and element dimensions in real time to inspect curve alignment.
- **Copy-Paste CSS `calc()` Snippets:** Generates production-ready, dynamic CSS custom property snippets ready for your design system.
- **Extreme-Case Handling:** Accurately clamps inner radii to `0px` when padding is greater than or equal to the outer radius.
- **Zero Dependencies:** Pure vanilla stack without frameworks, virtual DOM overhead, or bundlers.
- **Accessible Controls:** Built using semantic form inputs with proper keyboard navigation and visual focus rings.

---

## CSS Implementation

Instead of hard-coding static pixel values across breakpoints, this tool provides the modern CSS token pattern to make your components self-calculating:

```css
.card {
  --card-radius: 24px;
  --card-padding: 12px;

  /* Outer container */
  padding: var(--card-padding);
  border-radius: var(--card-radius);
}

.card__inner {
  /* Inner radius dynamically scales with padding */
  border-radius: max(0px, calc(var(--card-radius) - var(--card-padding)));
}
```
