# Weather-forecast
# Weather Widget

A compact, self-contained hourly weather forecast page for embedding in a Notion dashboard.

Default location: **Kuala Lumpur, Malaysia**.  
Data: [Open-Meteo](https://open-meteo.com/) (no API key).

## File

- `weather.html` — single-file widget (HTML + CSS + JS)

## What it shows

- Current temperature, condition, humidity, wind, and “feels like”
- Next 24 hours by default (time, icon, temp, rain chance)
- Auto-refresh every 15 minutes
- Transparent page background so it sits cleanly on a Notion page

## Embed in Notion

Notion’s `/embed` block needs a **public URL**.

1. Host `weather.html` somewhere public:
   - GitHub Pages
   - Cloudflare Pages / Netlify Drop
   - Any existing site path, e.g. `https://yoursite.com/weather.html`
2. In Notion, type `/embed` and paste that URL.
3. Resize the block to about **400 × 520**.

Local files cannot be embedded directly.

## URL parameters

| Param   | Default        | Notes                          |
|---------|----------------|--------------------------------|
| `place` | Kuala Lumpur   | Display label only             |
| `lat`   | `3.139`        | Latitude                       |
| `lon`   | `101.6869`     | Longitude                      |
| `hours` | `24`           | Hours to show (6–48)           |

Examples:

```
weather.html
weather.html?hours=12
weather.html?place=Petaling%20Jaya&lat=3.1073&lon=101.6067&hours=18
```

## How it works

1. Reads `lat`, `lon`, `place`, and `hours` from the query string.
2. Fetches current + hourly forecast from Open-Meteo with timezone `Asia/Kuala_Lumpur`.
3. Maps WMO weather codes to short labels and emoji icons.
4. Renders the current card and a horizontally scrollable hourly strip.
5. Reloads data every 15 minutes.

## Requirements

- A browser that can reach `https://api.open-meteo.com`
- A public host if you want to embed it in Notion

No build step, dependencies, or API key.
