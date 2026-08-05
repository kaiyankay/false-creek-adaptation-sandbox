# Site data

The app loads only the files in `processed/`. Nothing is rasterised or
invented in the browser; the `raw/` folder is kept alongside as the
provenance record for every derived layer.

## raw/ — real sources

| File | Source |
| --- | --- |
| `dem.tif` | Site-clipped mosaic of City of Vancouver **LiDAR 2013** bare-earth tiles (0.5 m, EPSG:26910, CGVD28). |
| `site-boundary.geojson` | Official **CD-1 (454)** polygon from the CoV `zoning-districts-and-labels` dataset — the active (editable) site. |
| `building-footprints-2015.geojson`, `public-streets.geojson`, `bikeways.geojson`, `parks-polygon-representation.geojson`, `property-parcel-polygons.geojson`, `city-owned-properties.geojson`, `shoreline-2002.geojson` | City of Vancouver Open Data layers (site-window clips; `shoreline-2002` is citywide). |
| `source-manifest.json` | Provenance record for boundary + DEM (dataset ids, URLs, dates, CRS). |
| `context/*.geojson` + `context/context-manifest.json` | The same CoV datasets fetched for the larger context window (Cambie Bridge, W 2nd Ave, south blocks). |

## processed/ — derived layers used by the app

| File | Contents |
| --- | --- |
| `site-metadata.json` | Grid definition (380×260 cells @ 2.5 m, EPSG:26910), DEM stats, water levels, counts, provenance, warnings, `dataMode`. |
| `cells.json` | Columnar per-cell arrays: `baseType` (index into `typeTable`), `elevation` (m CGVD28), `flags` (active/editable/water/shoreline/bridge/edge bits), `ownership`, ordered `shorelineOrder`. |
| `buildings.json` | Real footprints as local-metre rings + schematic heights. |
| `bridge.json` | Cambie Bridge centreline (real) + schematic deck constants. |
| `water.geojson`, `shoreline.geojson`, `roads.geojson`, `paths.geojson`, `landuse.geojson`, `buildings.geojson` | Record copies of the derived/clipped layers (EPSG:26910). |

## Known derivations (also listed in site-metadata.json warnings)

- pedestrian-path cells are a 4.5 m band along the official shoreline-2002
  line (the seawall walkway has no dedicated public layer)
- building cells inside CD-1 (454) are classed `mixed-use` from the zoning
  district type; heights are schematic (20 m site / 10 m context)
- Cambie Bridge deck elevation (11 m) is schematic
- water is polygonised from the official shoreline line, not a water-body
  polygon dataset

## public-trees

- `processed/public-trees.json` — 830 surveyed trees inside the data window.
- Source: City of Vancouver Open Data **public-trees** (formerly street-trees),
  fetched 2026-07-15 via the Explore v2.1 export API (bbox filter); raw copy in
  `raw/context/public-trees.geojson`.
- Fields kept: position (reprojected EPSG:26910 -> site-local metres),
  surveyed `height_m`, and a DISPLAY-ONLY crown radius estimated from
  `diameter_cm` (r = 1.0 + cm x 0.035, clamped 1.2-5.0 m).
- Honest note: the dataset covers PUBLIC trees (streets and some public land);
  park interiors are sparsely covered — the map shows exactly what the city
  has surveyed, nothing invented.

City of Vancouver Open Data is used under the
[Open Government Licence – Vancouver](https://opendata.vancouver.ca/pages/licence/).
