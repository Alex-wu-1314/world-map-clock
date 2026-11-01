# World Time Map

An interactive, single-file world time map: view the current local time, UTC offset, and real day/night distribution for 1,600+ cities around the globe. No installation or internet connection required — just open the HTML file.

## Features

- **Live day/night terminator** — the shadow is computed from the real solar position (declination and hour angle) and moves smoothly over time, instead of using coarse timezone blocks.
- **1,605 cities** — capitals and major cities worldwide, with coordinates, IANA timezones, and population tiers embedded.
- **Flat map + 3D globe** — switch between an equirectangular 2D map and a rotatable 3D globe with one click.
- **Zoom and pan** — mouse wheel, drag, and two-finger gestures, up to 6× zoom.
- **Hover details** — hover over a city to see its local date/time, timezone name, difference from the reference clock, and today's sunrise/sunset.
- **City search** — search by Chinese or English name to focus and zoom to a city.
- **Continent filters** — quickly filter by Asia, Europe, Africa, North America, South America, Oceania, Russia, or Antarctica, with automatic zoom to the region.
- **Local and UTC reference clock** — toggle the clock at the top between local time and UTC for easy timezone conversion.
- **Pinned cities** — pin cities of interest to compare their times at a glance.
- **Bilingual UI** — switch between Chinese and English; the preference is stored locally.
- **Fully offline** — city data, map outline, styles, and all logic are embedded in a single HTML file, with no external requests.

## Usage

Open `world-time-map.html` directly in a browser:

```bash
# Windows
start world-time-map.html

# macOS
open world-time-map.html

# Linux
xdg-open world-time-map.html
```

You can also serve it with any static server:

```bash
python -m http.server 8000
# then visit http://localhost:8000/world-time-map.html
```

### Interactions

| Action | Description |
| --- | --- |
| Mouse wheel / pinch | Zoom in and out around the cursor |
| Drag | Pan the map |
| Hover a city | Show local time, timezone, sunrise and sunset |
| Click a city | Pin or unpin it |
| "Globe Mode" button | Toggle between flat map and 3D globe |
| "EN / 中" button | Switch UI language |

## Technical Notes

- Pure HTML / CSS / JavaScript with no dependencies and no build step.
- The map is drawn with SVG; the night shading, sun position, and 3D globe use a mix of Canvas and SVG rendering.
- The terminator is derived from an approximate solar-position algorithm (declination plus hour angle), with lookup tables (LUTs) to speed up per-pixel rendering so it stays smooth at one update per second.
- City labels use a collision-avoidance layout that adapts font size and density while zooming.
- Supports high-DPI displays, wide-screen responsive layouts, and touch gestures.

## Project Structure

```
world-map/
├── world-time-map.html   # Everything: styles, city data, map and interaction logic
└── README.md
```

## Data

City data includes Chinese/English names, country or region, continent, coordinates, IANA timezone, and population tier, embedded in `window.CITIES_DATA` inside the HTML. Time conversion relies on the browser's built-in `Intl` timezone database, so daylight saving time (DST) transitions are handled automatically.

## License

No open-source license has been specified yet. Please contact the author before public reuse or redistribution.
