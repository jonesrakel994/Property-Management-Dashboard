# Property Management Dashboard

Static HTML/CSS build of the "Property Management Dashboard" design. No build
step, no dependencies beyond a Google Fonts CDN link — just open `index.html`
in a browser, or deploy the folder as-is.

## Files
- `index.html` — semantic markup (aside/nav, main, header, section/article)
- `style.css` — all styling, using CSS custom properties for the bar chart
- `README.md` — this file

## On the Figma link
The Figma URL you shared still can't be opened by my tools — it's blocked by
Figma's bot detection at the network level, which is unrelated to file
sharing permissions. This build is instead based on the high-resolution PNG
export, which gave enough detail to correct one of my own earlier mistakes
(see point 1 below). If you're able to pull exact values from Figma's Dev
Mode inspector (spacing, hex codes, font family/weights) for any component,
send them over and I'll tighten this to match exactly.

## Inconsistencies found in the design, and how they were handled

1. **"Number of Sales" delta arrow was pointing the wrong way.** The value
   went from 950 last month to 320 now — a real decrease — and the badge
   correctly uses the red/negative color. But the arrow glyph inside it
   pointed up-right (↗), the same direction used on the two cards that
   *increased*. I corrected the arrow to point down-right (↘) so the icon
   agrees with the color and the underlying numbers.

   *(Note: in an earlier pass, before I had this clearer export, I
   mistakenly "fixed" this the other way — recoloring the badge to green.
   That was wrong; the red color was correct all along. This version
   supersedes that one.)*

2. **The "20%" label on that same card doesn't match the actual math.**
   950 → 320 is roughly a 66% decrease, not 20%. I left the number as-is
   rather than inventing a replacement, since I can't be sure whether "20%"
   or "950" is the typo — but it's worth confirming against your real data
   source before shipping.

3. **All three Maintenance Requests shared the same Request ID (`MR-001`)**
   — almost certainly a copy-paste artifact, since three distinct requests
   shouldn't share one ID. Corrected to `MR-001`, `MR-002`, `MR-003`.

4. **The third "Last Transactions" row was cropped** at the bottom edge of
   both exports (thumbnail, title, and `$20K` visible, but no timestamp). I
   filled in `8 Sep 2024, 9:29` following the pattern of the rows above it —
   flagging this as inferred, not confirmed, content.

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
  display face in the export; body text uses Inter. Without Dev Mode access
  I can't confirm the exact family/weights Figma has specified.
- The bar chart and donut chart are hand-built with CSS/SVG (no charting
  library), matching the visual without adding a dependency.
