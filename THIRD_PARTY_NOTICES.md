# Third-party notices

This independent add-in includes GF Gear Generator 1.1.1, originally installed at
`%APPDATA%/Autodesk/ApplicationPlugins/GFGearGenerator.bundle/Contents/`.

- Upstream: https://github.com/CenturySturgeon/GF-Gear-Generator
- Copyright (c) 2022, CenturySturgeon. All rights reserved.
- Source credits: Juan Gras, Michael Truell, Mervill.
- License: BSD 3-Clause. The complete, unabridged license is in [GF-Gear-Generator-LICENSE.txt](GF-Gear-Generator-LICENSE.txt).
- File: `vendor/gfgear.py`. Original and bundled SHA-256 hashes: `vendor/provenance.json`.
- Changes: outer exception handlers in `extruir` and `combine` propagate errors to
  the batch controller instead of displaying dialogs and returning no result.
  The successful geometry path, tooth calculations and sample resolution are unchanged.
  Exact changes: `vendor/changes.patch`.

GF Gear Batch is an independent integration; no endorsement by the upstream authors
or Autodesk is implied. The original installed add-in is neither modified nor required
to be running. Its commands, caches, visibility helpers and lifecycle are not invoked.

The Batch evaluation license does not cover GF-derived code or its changes.
GF-derived materials remain BSD 3-Clause, including vendor/gfgear.py
and vendor/changes.patch. No rights granted by BSD are restricted.

The vendor files referenced above are inside the add-in ZIP in Releases.
