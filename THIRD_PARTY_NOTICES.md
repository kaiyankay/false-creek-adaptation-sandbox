# Third-party notices

This application bundles **no third-party map engine code or assets**. The
projects below were reviewed as design/implementation references; they are
recorded here for provenance and attribution of ideas. No source files from
them are distributed with this project.

| Project | License | Reviewed for |
| --- | --- | --- |
| [harp.gl](https://github.com/heremaps/harp.gl) (HERE) | Apache-2.0 | white/reduced map theme value hierarchy |
| [maptalks.three](https://github.com/maptalks/maptalks.three) | MIT | polygon extrusion / line ribbon / merged mesh patterns |
| [Tangram](https://github.com/tangrams/tangram) (Mapzen) | MIT | scene style profiles, layer/filter/style separation |
| [procedural-gl-js](https://github.com/felixpalmer/procedural-gl-js) | MIT | zoom-dependent level of detail, ortho zoom handling |
| [deck.gl](https://github.com/visgl/deck.gl) (OpenJS/vis.gl) | MIT | radius picking, localized interaction overlays, update triggers |

Bundled runtime dependencies include React, React Three Fiber, Drei,
Three.js, Zustand, Turf.js and pdf.js — each under its own open-source
license.

City of Vancouver Open Data (DEM tiles, zoning, streets, bikeways, parks,
building footprints, shoreline, parcels, public trees) is used under the
[Open Government Licence – Vancouver](https://opendata.vancouver.ca/pages/licence/).

Evidence documents under `/evidence` are unmodified official public
publications (City of Vancouver, Province of British Columbia, Fisheries and
Oceans Canada); copyright remains with their respective publishers.
