# Malaysia New Launches Explorer

**Live site: [malaysia-launches-explorer.vercel.app](https://malaysia-launches-explorer.vercel.app)**

Interactive map of new residential property launches across Peninsular Malaysia, with a Claude-powered project assistant and public transit overlays.

Built as an integration project at **EdgeProp Malaysia**, combining Mr. Hock's property launches dataset with additional data layers (transit, demographics, amenities).

---

## Features

- **2,818 property projects** plotted on a clustered interactive map
- **Claude-powered Project Assistant** — ask questions like "condos under RM600k near an LRT station" and get filtered results from the live dataset
- **Transit network overlay** — LRT, MRT, KTM Komuter, KL Monorail, BRT Sunway Line, ERL, and ECRL (under construction), with real OSM track geometry
- **Heatmap** — state-level shading to visualise regional project density
- **Upcoming:** DOSM district-level demographics toggle, amenities layer

---

## Tech stack

| Layer | Tool |
|---|---|
| Map | [Leaflet 1.9.4](https://leafletjs.com) + [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster) |
| Transit geometry | OpenStreetMap via Overpass API |
| AI assistant | [Claude API](https://docs.anthropic.com) (claude-haiku-4-5) via Vercel serverless |
| Hosting | [Vercel](https://vercel.com) |

---

## Local development

```bash
npm install -g vercel
vercel dev
```

The app runs at `http://localhost:3000`. The AI assistant requires a `CLAUDE_API_KEY` environment variable (set it in a `.env.local` file or via `vercel env`).

```
CLAUDE_API_KEY=sk-ant-...
```

---

## Project structure

```
├── index.html        # Single-page app (map, UI, transit rendering)
├── transit.json      # OSM transit route geometry (16 lines)
├── api/
│   ├── ask.js        # Claude-powered project assistant (serverless)
│   ├── geo.js        # Geo lookup endpoint (serverless)
│   └── data.json     # Full project dataset (server-side)
└── package.json
```

---

## Data sources

- **Property launches** — EdgeProp Malaysia internal dataset
- **Transit geometry** — [OpenStreetMap](https://www.openstreetmap.org) contributors, via [Overpass API](https://overpass-api.de)
- **State boundaries** — OpenStreetMap
- **Demographics** — [DOSM](https://www.dosm.gov.my) (upcoming)

---

## Related

- Original standalone analytics dashboard: [thomasvanpul/malaysia_map](https://github.com/thomasvanpul/malaysia_map)
