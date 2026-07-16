# Property Management Dashboard

Static HTML/CSS build of the "Property Management Dashboard" design. No build
step, no dependencies beyond a Google Fonts CDN link — just open `index.html`
in a browser, or deploy the folder as-is.

## Files
- `index.html` — semantic markup (aside/nav, main, header, section/article)
- `style.css` — all styling, using CSS custom properties for the bar chart
- `README.md` — this file

## Accessibility pass
- Landmarks: `aside` (nav), `main`, `header`, `section`/`article`.
- All icon-only buttons/links have `aria-label`.
- The search input has an associated (visually hidden) `<label>`.
- The bar chart and donut chart each have `role="img"` with a descriptive
  `aria-label`, since the visuals are decorative SVG rather than a real
  `<table>` of data.
- Color is never the only signal on the stat deltas — the up/down arrow
  glyph reinforces the badge color.
- All interactive elements have a visible `:focus-visible` state.
- `prefers-reduced-motion` is respected.

## Known simplifications
- Avatar and property thumbnail images are placeholder images (pravatar.cc /
  Unsplash) since no real assets were supplied.
- Heading font is set to Poppins as a close approximation of the rounder
  display face in the export; body text uses Inter. 
- The bar chart and donut chart are hand-built with CSS/SVG (no charting
  library), matching the visual without adding a dependency.
