# Clipper Templates

Site-specific templates for Obsidian Web Clipper.
Import a template: Web Clipper settings → Templates → "+" → switch to JSON view → paste.

| File | Site | Auto-applies on | Extracts |
|---|---|---|---|
| `flippa.json` | Flippa | `flippa.com/*` | Title, price, metrics, description, financials, traffic, monetization |

## Selectors used — Flippa

| Field | Selector | Confidence |
|---|---|---|
| Title | `h2` | ✅ Stable — top-level heading |
| Description | `meta[og:description]` | ✅ Stable — meta tag |
| Price | `.bid-box-price` | ✅ Stable — dedicated class |
| Key metrics | `#properties-summary` | ✅ Stable — dedicated ID |
| Full description | `#description-section` | ✅ Stable — dedicated ID |
| Financials table | `#financials-detail-table` | ✅ Stable — dedicated ID |
| Traffic insights | `#collapse-traffic_insights` | ⚠️ Fragile — accordion div, may change |
| Monetization | `#collapse-monetization_methods` | ⚠️ Fragile — accordion div, may change |

⚠️ Accordion divs (`#collapse-*`) are rendered client-side. If a field is empty after clipping,
the page may not have fully loaded. Wait 2–3 seconds after page load before clipping.

## Adding a new template

1. Save the page as "Webpage, HTML only" in your browser
2. Use the workflow in `_workflows/web-clipper-template.md`
3. Paste the generated JSON here as `<domain-slug>.json`
4. Update this README
