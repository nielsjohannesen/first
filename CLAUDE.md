# Pricing Game — Firms & Markets

## What this is
A single-page interactive game for an MBA course on Firms & Markets.
Student groups manage 10 shops and try to find the profit-maximising price
over 5 rounds, learning to infer a hidden demand function from noisy sales data.

## How to access the live site
Hosted on GitHub Pages. URL: https://nielsjohannesen.github.io/first/

## The game mechanics
- Groups enter a group number at the start (1–999)
- They see historical sales data at 3 pre-set prices ($15, $20, $25)
- Over 5 rounds they set one price → all 10 shops simulate sales independently
- At the end they can copy their results as tab-separated data (pastes into Excel)

## Demand model (hidden from students)
- Q per shop = 200 − 5×P + noise,  noise ~ N(0, 8)
- Unit cost = $20 per unit
- Profit-maximising price = $30  (yields ~50 units/shop, ~$500 profit/shop/round)
- Noise is seeded by (group number, round, shop) so results are reproducible

## Parameters to calibrate
All parameters are defined at the top of `index.html` (lines ~50–57):
- `A`, `B` — demand intercept and slope
- `NOISE_SD` — noise per shop
- `COST` — unit variable cost
- `HIST_P` — the three historical prices shown at the start
- `ROUNDS`, `SHOPS` — number of rounds and shops

## Code structure
Everything lives in one file: `index.html`
- Top: CSS styling (`:root` variables make colours easy to change)
- Middle: HTML shell (`<div id="app">`)
- Bottom: JavaScript — simulation logic, game state, rendering, copy-to-clipboard

## Ideas for future improvements (discussed with professor)
- Calibrate demand parameters once professor decides on target price range
- Add a professor summary page (password-protected or hidden URL)
- Add a chart showing price vs. profit as rounds accumulate
- Option to add fixed costs per shop per round
- Tweak student-facing instructions
- Consider a mailto / Formspree button so students can email results directly
