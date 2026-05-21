# Victoria Licensed Venue Finder

Inspector planning tool for gambling and liquor venues across Victoria.

## Demo

Live demo: https://kmorrish.github.io/venue-finder/

## What it does

- Displays licensed venues across Victoria on an interactive map
- Clusters venues by density — zoom in to expand
- Search by venue name, suburb, or street
- Filter by venue type (Gambling / Liquor / Both)
- Filter by inspector zone or suburb
- Click any venue for licence details

## How it works

The app reads from `venues.geojson` on load. In production this file is regenerated nightly by a scheduled script that queries the SQL Server database.

## Files

- `index.html` — the entire application (Leaflet.js, no framework needed)
- `venues.geojson` — venue data (sample data for demo; replaced by nightly export in production)

## Production setup

1. Host `index.html` and `venues.geojson` on IIS
2. Schedule `export_venues.py` (provided separately) to run nightly via Windows Task Scheduler
3. The script queries SQL Server and overwrites `venues.geojson`
4. No other infrastructure required

## Stack

- [Leaflet.js](https://leafletjs.com/) — mapping
- [Leaflet.markercluster](https://github.com/Leaflet/Leaflet.markercluster) — clustering
- [OpenStreetMap](https://www.openstreetmap.org/) — basemap tiles
- No build tools, no framework, no licensing costs
