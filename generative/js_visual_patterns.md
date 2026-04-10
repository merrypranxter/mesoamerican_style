# JavaScript Visual Patterns — Mesoamerican Style

## Canvas / SVG patterns
- **Register bands**: Render 3–7 horizontal bands, each with its own motif seed.
- **Glyph tiles**: Create a tile atlas (N glyph variants) and stamp them with controlled repetition.
- **Step-fret borders**: Polyline border that turns at quantized steps; mirror top/bottom.

## Useful abstractions
- `makeGrid(w, h, cellSize)` for modular layout
- `quantize(v, step)` for stair-stepped geometry
- `mirrorX(shape)` / `mirrorY(shape)` for symmetry controls

## Generative constraints
- Use limited palette selection from `palette/palettes.json`.
- Keep stroke widths chunky; add inner groove line.
