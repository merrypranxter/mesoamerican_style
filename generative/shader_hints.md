# Shader Hints — Mesoamerican Style

## Core shader mapping ideas
- **Signed distance fields (SDF)**: Build glyph blocks and step-frets from rectangles and unions/subtractions.
- **Relief carving**: Convert SDF to height; derive normals from height gradient; light with raking directional light.
- **Pigment-in-recesses**: Use curvature/occlusion proxy (e.g., based on height or SDF edges) to push color into grooves.
- **Chisel noise**: Add micro-noise aligned to edges; use anisotropic noise along tangent direction.

## Procedural modules
- `stepFret(p)` -> returns distance/coverage for a key-pattern polyline
- `glyphTile(uv, seed)` -> subdivides tile; places hooks/S-curves
- `cartoucheFrame(uv)` -> frame mask for border band

## Animation suggestions
- Slow phase drift in pigment intensity (not geometry) to feel ancient/ritual.
- Subtle erosion over time: increase edge roughness; reduce relief depth.
