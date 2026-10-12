# AGENTS.md
Context for AI coding tools working in this repository. Per-tool files should point here instead of duplicating it.

## Project
Farm2Table is a browser-based app that makes agricultural and environmental sensor data as easy to explore as a map. Users find sensor stations on an interactive map, inspect current conditions, view time-series data, compare locations, and investigate relationships between variables (for example rainfall and soil moisture) without downloading CSVs or writing scripts. It builds on the open-source Ear2Earth platform and is also meant to support agricultural and environmental education.

Main features:
- Interactive map of sensor stations, with last-update time and device status
- Per-station sensor list with metadata (type, units, depth/height, deployment info, last communication)
- Interactive time-series plots (24 hours, 7 days, 30 days, season, custom range) with zoom, pan, and hover
- Comparison of multiple variables or multiple stations
- CSV export of selected data
- Works on desktop, tablet, and mobile

## Setup commands
- Install deps: `pnpm install`
- Start dev server: `pnpm dev`
- Run tests: `pnpm test`

## Code style
- TypeScript strict mode
- Single quotes, no semicolons
- Use functional patterns where possible
