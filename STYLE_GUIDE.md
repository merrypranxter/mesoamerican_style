# Mesoamerican Style Guide (for generative systems)

This guide describes stylistic signals and constraints that help a generator reliably evoke "Mesoamerican" visual language *without* relying on a single culture/period as a literal copy.

## Core visual signals
- **Stone + pigment**: carved relief forms with mineral pigments in recesses.
- **Glyph logic**: symbols are compact, modular, and repeatable (tileable blocks).
- **Step-fret geometry**: right-angle stair-stepped edges and nested key patterns.
- **Frontal symmetry + stacked registers**: compositions read like codex pages or temple friezes.
- **High-contrast edges**: incised outlines; shadowed grooves.
- **Material cues**: jade, obsidian, basalt, limestone, cinnabar.

## Composition rules
- Prefer **bands/rows (registers)** over floating objects.
- Use **central axis symmetry**, then break it with small asymmetries.
- Frame content in **cartouches** and **border glyph bands**.
- Scale hierarchy: primary deity/figure largest, secondary symbols smaller.

## Shape language
- Curves are deliberate: serpents, spirals, feather bundles.
- Many forms can be reduced to: rectangles, trapezoids, hooks, S-curves.
- Use **negative space** as a carved channel.

## Texture + lighting cues
- Carving: micro-chipped edges, worn corners, tool marks.
- Lighting: raking light from a low angle to emphasize relief.

## Anti-patterns (avoid)
- Avoid modern "Aztec calendar" cliché stamping everywhere.
- Avoid generic "tribal tattoo" shapes.
- Avoid Euro-medieval ornament vocabulary (acanthus, baroque scrollwork).

## Generator knobs (suggested)
- `reliefDepth`: 0.1–0.8
- `glyphDensity`: 0.2–0.9
- `symmetry`: 0.0–1.0
- `stepFretStrength`: 0.0–1.0
- `pigmentInRecesses`: 0.0–1.0
