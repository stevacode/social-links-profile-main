# Frontend Mentor - Social links profile solution

This is a solution to the [Social links profile challenge on Frontend Mentor](https://www.frontendmentor.io/challenges/social-links-profile-UG32l9yoQH).

## Table of contents

- [Overview](#overview)
  - [The challenge](#the-challenge)
  - [Screenshot](#screenshot)
  - [Links](#links)
- [My process](#my-process)
  - [Built with](#built-with)
  - [What I learned](#what-i-learned)
  - [Continued development](#continued-development)
  - [Useful resources](#useful-resources)
- [Author](#author)

## Overview

### The challenge

Users should be able to:

- See hover and focus states for all interactive elements on the page
- View the optimal layout for the content depending on their device's screen size

### Screenshot

![](./preview.png)

### Links

- Solution URL: [Add your Frontend Mentor solution URL here](#)
- Live Site URL: [Add your live site URL here](#)

## My process

### Built with

- Semantic HTML5 markup
- CSS custom properties (design tokens for colors and spacing)
- Flexbox
- Self-hosted Inter variable font via `@font-face`
- Responsive, mobile-friendly layout

### What I learned

The part I spent the most time on was **centering the card** — and it taught me
something I had wrong in my head. I assumed that because `body` was a flex
container with `align-items: center`, the card would center automatically. But
flex alignment only affects a container's *direct* children. My direct child was
`<main>`, not `.card`. Once I made `<main>` itself a flex container, the card
finally centered:

```css
main {
  width: 100%;
  display: flex;
  justify-content: center;
}
```

I also went down a wrong path trying to stop the bio text from wrapping. I
reached for `white-space: nowrap`, but that didn't *fix* anything — it just
pushed the text out past the edge of the card and caused horizontal scrolling.
That was a useful lesson: `nowrap` doesn't create space, it only changes what
happens when there isn't enough of it. The real issue was the layout/spacing
around the text, not the text itself.

Finally, I self-hosted the Inter **variable** font, which let me cover every
weight with a single `@font-face` block using a weight *range* instead of one
value:

```css
@font-face {
  font-family: "Inter";
  src: url("../assets/fonts/Inter-VariableFont_slnt,wght.ttf") format("truetype");
  font-weight: 100 900;
  font-display: swap;
}
```

A small but important detail here: the `url()` path is resolved relative to the
**CSS file**, not the HTML file. Since my stylesheet lives in `/css/`, I needed
`../` to step back out before reaching `/assets/fonts/`.

### Continued development

- Getting more comfortable deciding when a text wrap is a real bug versus normal,
  healthy responsive behavior
- Practicing `rem`/`%` based sizing so layouts stay flexible across screen sizes
- Using `:focus-visible` consistently so keyboard users always get a clear focus state

### Useful resources

- [MDN – @font-face](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face) - Clear reference for self-hosting fonts and understanding the descriptors.
- [MDN – :focus-visible](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible) - Helped me understand why keyboard focus states matter.
- [CSS-Tricks – A Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) - My go-to whenever I need to reason about flex alignment.

## Author

- Frontend Mentor - [@stevacode](https://www.frontendmentor.io/profile/stevacode)
- GitHub - [@stevacode](https://github.com/stevacode)