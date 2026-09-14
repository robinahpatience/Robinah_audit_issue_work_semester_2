# JK Restaurant — Website Prototype

A small, connected website for JK Restaurant, a Ugandan kitchen in Mukono.
Built for the Semantic HTML Prototype and Responsive Interfaces assignments.

## Structure

```
jk-restaurant/
├── index.html      Home
├── menu.html        Menu
├── about.html       About
├── contact.html      Contact & reservations (reservation form)
├── css/style.css    External stylesheet, mobile-first
├── js/nav.js        Accessible mobile nav toggle
└── images/          Original SVG dish illustrations
```

## How to view it locally

Open `index.html` in a browser, or serve the folder with any static
server (e.g. `python3 -m http.server` from inside the folder).

## Publishing to GitHub Pages

1. Create a new public GitHub repository, e.g. `jk-restaurant`.
2. Push this folder's contents to the repository's `main` branch.
3. In the repo settings, enable **GitHub Pages** for the `main` branch
   (root folder).
4. Your live site will appear at `https://<username>.github.io/jk-restaurant/`.

---

## Submission text — Assignment 1: Semantic HTML Prototype

**Repository:** `https://github.com/<your-username>/jk-restaurant`

**1. Pages created:** Home (`index.html`), Menu (`menu.html`), About
(`about.html`), and Contact & Reservations (`contact.html`).

**2. Navigation:** A navigation bar appears in the `<header>` of every
page and links to all four pages. The link for the current page is
marked with `aria-current="page"` so users (and assistive technology)
can tell where they are. On small screens the nav is tucked behind a
toggle button; on wider screens it is shown as a permanent horizontal
bar.

**3. Semantic HTML elements used:** `<header>` and `<nav>` for the
site header and navigation on every page; `<main>` to wrap each
page's primary content; `<section>` to group related content (hero,
highlights, menu groups, contact details); `<article>` for
self-contained items such as dish cards and team member bios;
`<aside>` for the "at a glance" panel on the About page; `<footer>`
for the site footer on every page; `<fieldset>`/`<legend>` and `<dl>`
for grouped form controls and contact details.

**4. Form:** The Contact page (`contact.html`) contains a reservation
form that collects the guest's full name, email address, phone
number, preferred date and time, party size, seating preference, and
an optional note for allergies or special requests.

**5. Accessibility decisions:**
- Every form input has a `<label>` associated with it via matching
  `for`/`id` attributes, and the optional notes field is linked to a
  hint via `aria-describedby`.
- All images (dish illustrations) have meaningful `alt` text
  describing the dish rather than the file name.
- Headings follow a logical order (`<h1>` once per page, `<h2>` for
  major sections, `<h3>` for individual items) with no levels
  skipped.
- Link text is descriptive ("View our menu", "Reserve a table")
  rather than "click here".
- A "Skip to main content" link is provided for keyboard users, and
  the mobile nav toggle uses `aria-expanded`/`aria-controls` so
  screen readers know whether the menu is open.

---

## Submission text — Assignment 2: Responsive Interfaces

**Repository:** `https://github.com/<your-username>/jk-restaurant`

**Deployed site:** `https://<your-username>.github.io/jk-restaurant/`
*(add once GitHub Pages is enabled)*

**Responsive changes:** The site is built mobile-first: the base CSS
in `style.css` targets small screens (single-column stacked layout,
collapsed navigation behind a toggle button), then two `min-width`
media queries progressively enhance the layout — a 640px breakpoint
switches info cards and dish cards to a two-column grid, and a 900px
breakpoint turns the navigation into a permanent horizontal bar and
switches the hero and menu/about sections to a side-by-side Flexbox
layout. Flexbox is used for the header, nav list, hero layout, and
form rows; CSS Grid is used for the dish-highlight and info-card
grids. Typography uses `clamp()` for headings so text scales smoothly
between screen sizes, and all images/illustrations resize with
`max-width: 100%`.

**Testing:** Tested at 375px (mobile), 768px (tablet) and 1440px
(desktop) widths using browser dev tools.

**Fix made:** At the tablet width, the reservation form's paired
fields (email/phone, date/time) were stacking awkwardly with too much
empty space. Adding a `.form-row--split` class that switches from a
column to a row layout at the 640px breakpoint fixed the spacing and
kept the fields aligned.

**Accessibility:** Colour choices keep text (`#f3e9dc` and
`#cbb9a4`) on the dark background (`#241712`) well above WCAG AA
contrast for body text, and interactive elements use a visible
`:focus-visible` outline in amber so keyboard focus is always clear.
`prefers-reduced-motion` is respected in case motion is added later.
