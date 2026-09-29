# Bridge Collective

A single-page landing site. No build step, no dependencies — open `index.html` in a browser.

## Structure

```
index.html          markup + inline menu script
style.css           all styles
images/
  favicon-32x32.png favicon
```

## Layout

The page is a CSS Grid: `body` is a three-row grid (`--header-h` / `1fr` / `auto`),
and `.layout` splits into a 45% hero column and a 1fr stat column. `.stats` is a
`1fr 1fr` grid with `grid-auto-rows: minmax(280px, 1fr)` so the four tiles fill the
remaining height evenly.

Below `860px` both grids collapse to block flow, tiles stack with top borders, and
the nav switches from a right-side slide-in panel to a centered drop-down.

Design tokens live in `:root` at the top of `style.css` — colors, the `--gutter`
spacing step, and `--menu-w` (tuned to one stat column so the panel aligns with the
grid).

## Menu

Vanilla JS at the bottom of `index.html`. It toggles `menu-open` on `<html>`, which
drives the panel, the scrim, and `overflow: hidden` on the root. Closes on scrim
click, on link click, and on `Escape` (which returns focus to the toggle). When
closed the panel is `visibility: hidden`, so it stays out of the tab order.

## Placeholder links

Nav and stat links point at in-page fragments. Three targets do not exist yet and
will need sections added:

- `#partners`
- `#annual-report`
- `#donate`

`#top`, `#about` (hero) and `#our-work` (stat grid) already resolve. Icons are
inlined SVGs in the HTML so they inherit `currentColor`; only the favicon lives in
`images/`.
