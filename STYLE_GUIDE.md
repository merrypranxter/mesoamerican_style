# Mesoamerican Style Guide (for generative systems)

This guide describes stylistic signals and constraints that help a generator reliably evoke Mesoamerican visual language. It covers both pan-cultural principles and culture-specific distinguishing features.

---

## Core Visual Signals (Pan-Mesoamerican)

- **Stone + pigment**: carved relief forms with mineral pigments in recesses.
- **Glyph logic**: symbols are compact, modular, and repeatable (tileable blocks).
- **Step-fret geometry**: right-angle stair-stepped edges and nested key patterns.
- **Frontal symmetry + stacked registers**: compositions read like codex pages or temple friezes.
- **High-contrast edges**: incised outlines; shadowed grooves.
- **Material cues**: jade, obsidian, basalt, limestone, cinnabar, turquoise.
- **Scale hierarchy**: primary deity/figure largest, secondary symbols smaller.
- **Raking light**: compositions designed to be seen by low-angle light; shadows create meaning.

---

## Composition Rules

- Prefer **bands/rows (registers)** over floating objects.
- Use **central axis symmetry**, then break it with small asymmetries.
- Frame content in **cartouches** and **border glyph bands**.
- Scale hierarchy: primary deity/figure largest, secondary symbols smaller, text smallest.
- Ground plane: most figures stand on a baseline; use the baseline to anchor.
- **Horror vacui in Classic Maya**: fill every background space; in other cultures, empty space is acceptable.

---

## Shape Language

- Curves are deliberate: serpents, spirals, feather bundles.
- Many forms can be reduced to: rectangles, trapezoids, hooks, S-curves.
- Use **negative space** as a carved channel.
- Quetzal feathers: long tapered strokes in radial fans; iridescent green.
- Skulls: integrated rhythmically into ornament — not horror imagery.

---

## Texture + Lighting Cues

- Carving: micro-chipped edges, worn corners, tool marks.
- Lighting: raking light from a low angle (15–30°) to emphasize relief depth.
- Pigment-in-recesses: dark channels accumulate pigment; raised surfaces = stone color.
- Weathering: patina on stone; plaster flaking; pigment surviving in protected recesses.

---

## Culture Quick-Reference: Distinguishing Visual Marks

| Culture          | Primary Medium          | Line Quality            | Key Motif                   | Color Signature                       |
|------------------|-------------------------|-------------------------|-----------------------------|---------------------------------------|
| **Aztec**        | Stone + codex           | Bold angular black      | Xicalcoliuhqui scroll       | Black/red/turquoise                   |
| **Maya Classic** | Stone relief + mural    | Flowing curvilinear     | Waterlily scroll + glyphs   | Maya Blue + cream + warm red          |
| **Maya Puuc**    | Stone mosaic facade     | Geometric, modular      | Stacked Chac masks          | Natural grey stone; no paint          |
| **Olmec**        | Basalt + jade sculpture | Rounded mass, minimal   | Were-jaguar cleft face      | Dark basalt + deep jade green         |
| **Teotihuacan**  | Mural painting          | Flat registers, frontal | Tlaloc goggle eyes          | Deep red ground + orange + blue-green |
| **Zapotec**      | Ceramic urn + relief    | Frontal, blocky         | Funerary urn headdress      | Grey-buff clay tones                  |
| **Mixtec**       | Codex strip             | Articulated, stiff      | Red-path codex narrative    | Cream/tan/red/turquoise               |
| **Toltec**       | Stone column + frieze   | Profile procession      | Atlantean warrior column    | Stone grey + warrior red              |
| **Veracruz**     | Relief + ceramic        | Organic scroll curves   | Interlocking double scroll  | Warm sandstone + ochre red            |

---

## Culture-Specific Style Directives

### When generating Aztec content:
- **Codex style**: bold black outlines, flat fills, NO shading gradients
- Primary colors: deep red + turquoise + yellow on black or cream ground
- Border default: **xicalcoliuhqui** (scrolled step-fret), not plain step-fret
- Feather work: dense radial quetzal fans; gold-and-green
- Skull use: rhythmic, patterned (tzompantli rows), not random
- Stone sculpture: massive, blocky, dense symbolic surface

### When generating Maya content:
- Classic period: flowing curves, elegant proportions, horror vacui background fills
- Always fill background with **waterlily scrolls** or **glyph blocks** (never leave blank)
- **Maya Blue** is sacred and rare; use as precious accent only
- Glyph columns: paired, L-R reading, rounded cartouche blocks
- Puuc style: sharp switch from plain lower zone to dense upper mosaic zone
- Long Count dates as decorative vertical column element

### When generating Olmec content:
- Think 3D mass, not surface pattern — rounded smooth volumes
- Were-jaguar: downturned trapezoidal mouth, V-cleft head, fat cheeks, large eyes
- Never use flat codex-style graphics for Olmec
- Colossal head: sphere with flattened back; features gently pressed forward
- Materials only: basalt grey or deep jade green; no bright colors

### When generating Teotihuacan content:
- Always horizontal registers — no diagonal arrangements
- Background fill: water drops, small flowers, small glyphs — never empty
- Figures are FRONTALLY oriented (not profile)
- Goggle eyes: concentric circles, never almond/slit
- Deep red (#B83A2E) as default mural background
- Talud-tablero as architectural profile: slope then vertical panel, stacked

### When generating Zapotec content:
- Funerary urn = the primary form; cylindrical jar + frontal deity face
- Headdress extends 2–3× face height above the face
- Strictly frontal, bilateral symmetry — zero profile or dynamic poses
- Cocijo: bifurcated projecting tongue, square mouth, large eyes
- Step-fret border bands as deep-cut geometric channels in stone

### When generating Mixtec content:
- Codex strip format: figures along a winding red-line reading path
- Warm palette: cream/tan bodies, deep red accents, turquoise objects
- No horror vacui — clean backgrounds with sparse labeled elements
- Turquoise mosaic objects: step-fret in small blue-green tiles
- Name-glyphs: day-sign + personal symbol attached near figure's head

### When generating Toltec content:
- Processional repetition — all figures face same direction, standardized
- Atlantean column: upright warrior figure, trefoil headdress, butterfly pectoral
- Chac Mool: horizontal reclining figure, 90° body twist, plate on abdomen
- Simple color: stone grey + warrior red; no complex pictographic fills
- Skull/serpent walls: strict alternating module repetition

### When generating Veracruz/Totonac content:
- Interlocking scroll as primary fill pattern — organic, energetic, all-over
- Niche pyramid: rectangular grid of deep shadow pockets on stepped faces
- Smiling figurine: exaggerated open smile, hollow clay, raised arms
- Ball game yoke: U-shaped stone form with carved scroll outer surface

---

## Generator Knobs (Suggested Parameters)

```
reliefDepth:        0.0–1.0   // 0=flat/codex, 1=deep sculptural
glyphDensity:       0.0–1.0   // density of glyph/symbol fill
symmetry:           0.0–1.0   // bilateral symmetry strength
stepFretStrength:   0.0–1.0   // prominence of step-fret border elements
scrollCurvature:    0.0–1.0   // 0=angular step-fret, 1=veracruz organic scroll
pigmentInRecesses:  0.0–1.0   // color fill in carved channels
horrorVacui:        0.0–1.0   // 0=plain background, 1=full Maya background fill
cultureBlend:       [0..1 per culture] // mix of cultural vocabularies
```

---

## Anti-Patterns (Avoid)

- **Avoid "Aztec calendar" as a single cliché stamp** — it is one specific late Aztec object; the tradition is vast
- Avoid generic "tribal tattoo" shapes (they are neither authentic nor culturally specific)
- Avoid Euro-medieval ornament vocabulary (acanthus, baroque scrollwork, Gothic tracery)
- Avoid shading gradients in codex-style work — flat fills only
- Do not mix Olmec sculptural mass with Aztec flat codex style in the same piece
- Do not apply Maya horror-vacui filling to Aztec or Teotihuacan compositions
- Avoid photoreal modern elements unless explicitly creating a culture-clash hybrid
- Do not use the goggle-eye (Tlaloc) motif for Maya figures — use Chaac's hook nose instead

