# Octagrid

A pen-friendly city-builder sandbox on a 45° grid. Everything lives in one file: open `index.html` in a browser.
Built for iPad with Apple Pencil, works with mouse and touch too.

- Roads (lane, street, avenue; straight or curved), buildings (7 types x 15 variants), ponds, parks, beaches, special buildings that fill any drawn shape, trees and props.
- **District**: draw an area, pick Homes / Downtown / Industry / Green and tap *Generate content*.
- City limit (320-960 m) with Block Runner style edges: a row of buildings or a lake with a beach.
- **Export map** writes an `octagrid-city` JSON file (version 2, units are grid cells, 1 cell = 10 m) that Block Runner can load as a preview.
- **Save** stores the city online. It only works when the page runs as a Claude artifact (it uses the artifact `db` and `downloads` capabilities). Outside Claude the city is kept in `localStorage`, and *Export map* shows the JSON text to copy instead of saving a file (a real download button is a good first task).

## Notes for development

- Single file, no build step, no dependencies. Sections in the script: geometry helpers, conflict rules, drawing, tools, strip UI, export, boot.
- Export format is documented by the `note` field in the exported file. `bounds` and `edges` describe the city limit.
- The `claude.use('db')` and `claude.use('downloads')` calls are wrapped in try/catch; outside Claude they resolve to nothing and the buttons hide or fall back.
