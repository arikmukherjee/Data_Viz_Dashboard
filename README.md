# Pulsar Data Viz Dashboard

A modern, fully responsive analytics dashboard built with pure HTML, CSS, and Vanilla JavaScript. No build tools or frameworks required — just open and run.

![Stack](https://img.shields.io/badge/HTML5-E34F26?style=flat&logo=html5&logoColor=white) ![Stack](https://img.shields.io/badge/CSS3-1572B6?style=flat&logo=css3&logoColor=white) ![Stack](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black) ![Stack](https://img.shields.io/badge/Chart.js-FF6384?style=flat&logo=chartdotjs&logoColor=white)

---

## Features

### Charts & Data Visualization
- **Bar Chart** — Revenue overview with gradient fills and hover highlighting
- **Line Chart** — User growth trend with area fill and smooth bezier curves
- **Doughnut Chart** — Regional distribution with a custom inline legend
- All charts animate on load and smoothly transition when data changes

### Interactive Filters
- **Period selector** — Toggle between Daily, Weekly, and Monthly datasets; all charts and KPIs update instantly
- **Category dropdown** — Switches the donut chart between All, Technology, Retail, and Finance distributions
- **Live Data toggle** — Simulates real-time data feeds with randomized fluctuations every 2.4 seconds, with a pulsing LIVE indicator

### KPI Stat Cards
- Four metric cards: Total Revenue, Active Users, Total Orders, Conversion Rate
- **Animated counters** — Numbers roll up with an eased animation on every data switch
- **Sparkline mini-charts** — Hand-drawn on Canvas, one per card, showing the current period trend
- Hover lifts cards and sweeps an accent-colored top border

### UI & Theming
- **Dark / Light mode** toggle in the sidebar footer
- **4 accent color themes** — Blue, Violet, Emerald, Amber; charts re-render immediately on change
- Loading skeleton shimmer on first open, followed by staggered reveal animations
- Sidebar navigation with active state indicators and a notification badge
- Responsive hamburger sidebar on mobile

### Export
- Each chart card has a download button that exports the chart as a PNG with the correct background for the current theme
- The top-right download button exports the bar chart directly

### Keyboard
- `⌘K` / `Ctrl+K` — Focuses the search bar

---

## Getting Started

No installation needed. Everything runs from a single HTML file.

```bash
# Clone or download the file, then open it
open index.html
```

Or serve it locally if you prefer:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080/index.html
```

---

## Project Structure

If you're working from the source files (before bundling):

```
/Pulsar_Data_Viz_Dashboard
├── index.html       # Markup: sidebar, topbar, chart canvases, skeleton
├── style.css        # All styles: tokens, themes, layout, animations
├── script.js        # Chart logic, filters, counters, live sim, export
└── data.json        # Sample data (also embedded in script.js for portability)
```

The `index.html` file is the fully self-contained version with CSS and JS inlined — no external files needed except the Chart.js CDN.

---

## Dependencies

| Library | Version | How loaded |
|---|---|---|
| [Chart.js](https://www.chartjs.org/) | 4.4.3 | CDN (`jsdelivr`) |
| [Syne](https://fonts.google.com/specimen/Syne) | — | Google Fonts |
| [DM Mono](https://fonts.google.com/specimen/DM+Mono) | — | Google Fonts |
| [DM Sans](https://fonts.google.com/specimen/DM+Sans) | — | Google Fonts |

No npm, no bundler, no framework.

---

## Sample Data

All data is embedded directly in `script.js` as a plain JavaScript object. Three period datasets are included:

- **Daily** — 7 data points (Mon–Sun)
- **Weekly** — 7 data points (Week 1–7)
- **Monthly** — 12 data points (Jan–Dec)

Each dataset contains revenue figures, user counts, and regional percentage breakdowns. To use your own data, edit the `DATA` object near the top of `script.js`.

---

## Customization

### Adding a new accent color
In `style.css`, add a new `[data-accent]` block:
```css
[data-accent="rose"] {
  --accent: #FB7185;
  --accent-glow: rgba(251,113,133,0.18);
  --accent-muted: rgba(251,113,133,0.10);
}
```
Then add a swatch button in `index.html` and wire it in the `initAccent()` function in `script.js`.

### Swapping in real data
Replace the `DATA` constant in `script.js` with a `fetch()` call to your own API:
```js
const DATA = await fetch('/api/analytics').then(r => r.json());
```

### Changing the live simulation interval
Find `setInterval` in the `startLive()` function and change `2400` to your preferred millisecond interval.

---

## Browser Support

Works in all modern browsers. Requires Canvas API support (all evergreen browsers).

---

## License

MIT — use it freely for personal or commercial projects.
