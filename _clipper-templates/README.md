# Clipper Templates

Site-specific templates for Obsidian Web Clipper.
Import a template: Web Clipper settings → Templates → "+" → switch to JSON view → paste.

| File | Site | Auto-applies on | Extracts |
|---|---|---|---|
| `flippa.json` | Flippa | `flippa.com/*` | Title, price, metrics, description, financials, traffic, monetization |
| `medium.json` | Medium & publications | `medium.com/*`, `towardsdatascience.com/*`, `levelup.gitconnected.com/*`, `betterprogramming.pub/*` | Title, author, published date, description, cover image, full article content |

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

## Selectors used — Medium

| Field | Source | Confidence |
|---|---|---|
| Title | `og:title` meta → `{{title}}` | ✅ Stable |
| Author | `meta[name='author']` → `{{author}}` | ✅ Stable |
| Published date | `article:published_time` meta → `{{published}}` | ✅ Stable |
| Description | `og:description` meta → `{{description}}` | ✅ Stable — extrait le sous-titre de l'article |
| Cover image | `og:image` meta → `{{image}}` | ✅ Stable |
| URL | → `{{url}}` | ✅ Stable |
| Article content | Readability → `{{content}}` | ✅ Stable — texte complet reformaté en Markdown |

⚠️ Medium masque parfois le contenu complet derrière le paywall. Dans ce cas, `{{content}}`
ne contiendra que l'extrait public. Clipper après s'être connecté à son compte Medium pour
obtenir le texte complet si l'article est dans ton abonnement.

## Adding a new template

1. Save the page as "Webpage, HTML only" in your browser
2. Use the workflow in `_workflows/web-clipper-template.md`
3. Paste the generated JSON here as `<domain-slug>.json`
4. Update this README
