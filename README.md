# PMTiles + Custom DEM Terrain with MapLibre

This project demonstrates how to visualize **vector tiles (PMTiles)** together with a **custom DEM terrain** in 3D using [MapLibre GL JS](https://maplibre.org/).

## Features
- Serve and visualize **PMTiles** (vector tiles) locally using XAMPP.
- Overlay **custom DEM raster tiles** (generated from a GeoTIFF → RGB tiles via `rio-rgbify`).
- Apply **3D terrain** with vertical exaggeration.
- Render **extruded buildings**, roads, land, and water layers.
- Interactive navigation with pitch, bearing, and zoom controls.

## Workflow
1. **DEM Preparation**
   - Convert DEM GeoTIFF → RGB tiles using [`rio-rgbify`](https://github.com/mapbox/rio-rgbify).
   - Create `TileJSON.json` pointing to your generated DEM tiles.
   - Serve the tiles with [XAMPP](https://www.apachefriends.org/).

2. **PMTiles Preparation**
   - Package vector data into `.pmtiles` format.
   - Place the `.pmtiles` file in the XAMPP root (e.g., `htdocs`).

3. **Visualization**
   - MapLibre loads:
     - **Vector data** from `.pmtiles`.
     - **Custom DEM** from `TileJSON.json`.
   - 3D terrain + extruded buildings are displayed.

## Running Locally
1. Install and start **XAMPP** (Apache server).
2. Copy the following files into `htdocs/`:
   - `index.html`
   - `20250915.pmtiles` (your vector tiles)
   - `TileJSON.json` + DEM tile folder (e.g., `dem_tiles_rgb/`).
3. Open in browser:

http://localhost/index.html

## Example Visualization
- Vector layers: water, land, roads, places labels.
- 3D buildings (extrusion based on height attributes).
- Custom DEM terrain (exaggerated 1.5×).

## Dependencies
- [MapLibre GL JS](https://maplibre.org/) v5.7.3
- [pmtiles.js](https://github.com/protomaps/PMTiles) v3.0.0

---

### Notes
- Ensure `TileJSON.json` correctly points to your DEM tiles (`http://localhost/dem_tiles_rgb/{z}/{x}/{y}.png`).
- Adjust `center`, `zoom`, `pitch`, and `bearing` in `index.html` as needed for your region.
