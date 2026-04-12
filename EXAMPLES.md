# Examples (text-only)

These are example *instructions* a generator can follow to produce culturally grounded Mesoamerican output.

---

## Generative Pattern Examples

### Example 1 — Aztec Border Band (step-fret)
- Build a xicalcoliuhqui scroll-fret border band, 12 units wide
- Alternate standard and mirror-image units every other tile
- Base color: Limestone (#C9C2B3). Groove shadow: Obsidian (#0D0D12). Scroll curl accent: Jade (#1E8F6A)
- Stroke weight: 3px. Fill the scroll interior with the jade accent color

### Example 2 — Maya Glyph Wall (horror vacui)
- 6 rows × 8 columns of Maya glyph blocks
- Each block: rounded square cartouche (corner radius 8%), inner border channel, main sign with superfix + subfix
- Main sign: randomly select from hooks, S-curves, dot clusters, interlocking curves
- Palette: carbon black outlines (#1C1C1C), cream background (#F2E8C6), Maya Blue (#1B6BA8) accents in 1 in 5 blocks
- Apply ambient occlusion approximation: fill deep channels with darker shade of cream

### Example 3 — Maya Cylinder Vase
- Cylindrical vase proportions: height = 1.8× diameter
- Top band (20% height): Primary Standard Sequence — 8 Maya glyph blocks in a row
- Middle band (60%): narrative scene — ruler figure in 3/4 view receiving offerings from smaller attendant figures; horror vacui background fills
- Bottom band (20%): geometric border — cauac sky band with alternating kin/akbal/star cartouches
- Palette: maya_polychrome; Maya Blue for background sky elements; blood red for costume fills

### Example 4 — Sun Stone Composition
- Circular composition, 800px diameter
- 7 concentric rings (innermost smallest):
  1. Center: Tonatiuh face (large facial features, tongue extended, clawed hands)
  2. Ring 2: 4 square cartouches at N/S/E/W with previous-sun symbols
  3. Ring 3: 20 equal-width day-sign cells (Cipactli through Xochitl)
  4. Ring 4: celestial/sky band — alternating star and jade-dot elements
  5. Ring 5: jade chalchihuitl dots repeating
  6. Ring 6: sun-ray triangles alternating with trapezoids
  7. Outer ring: two xiuhcoatl fire serpents — bodies wrap around; heads meet at bottom (6 o'clock)
- Stone: dark basalt grey (#2B2B2B). Pigment in deepest channels: cinnabar (#B1322E) and turquoise (#2AA8A1)

### Example 5 — Olmec Colossal Head Composition
- Spherical head form, 3:2 width:height ratio
- Flattened posterior (back half compressed)
- Features concentrated in frontal 60% of sphere
- Facial features: broad flat nose, full lips, heavy brow ridge, no jawline detail (absorbed into sphere)
- Helmet: flat-fronted rectangular helmet element on top 30% of sphere
- Material: dark basalt grey with very subtle cool-blue undertone in shadows
- Lighting: single directional light from 30° left angle; dramatic shadow on right hemisphere

### Example 6 — Teotihuacan Mural Register Composition
- Horizontal 3-band composition:
  - Top band (25%): sky band — rain drops falling, bird figures, speech-scroll volutes, blue-green (#1A7A72) background
  - Middle band (50%): main scene — frontal Tlaloc deity figure, goggle eyes, jadeite jewelry, gesturing hands; flanked by two smaller priests; water drops and maize plants fill all background space; deep red (#B83A2E) background
  - Bottom band (25%): border band — step-fret pattern alternating with chalchihuitl dots; limestone cream (#E8E0C0) background
- All outlines: carbon black (#1A1A1A), stroke weight 2px

### Example 7 — Zapotec Funerary Urn
- Cylindrical base (height 2× diameter)
- Frontal deity face attachment (Cocijo):
  - Face height: 1/3 of total object height
  - Eyes: large square eye sockets
  - Mouth: wide open square cavity with bifurcated tongue projecting 1/4 face height below
  - Headdress above face: 5 stacked layers extending another 2/3 of total height above face:
    1. Rectangular platform with step-fret incision
    2. Serpent mask layer
    3. Bird/feather crest
    4. Crossed-band element
    5. Top plume cluster
- Strict bilateral symmetry throughout
- Material: grey-buff clay (#B8A88A), natural fired surface texture

### Example 8 — Tajín Niche Pyramid in Shader
- Stepped pyramid silhouette (7 tiers)
- Each tier face: regular grid of rectangular niches
- Niche depth in height map: 0.6 (deep relative to face area)
- Niche interior: fully occluded (AO = 0 → darkest value #3A3028)
- Niche frame (raised): full light value (#D4B880)
- Animation: sun angle changes over 20 seconds — niche shadows grow/shrink as sun moves

### Example 9 — Mixtec Codex Strip
- Horizontal strip composition; 4:1 aspect ratio (wide)
- Bold red line (path) running along the middle of the strip
- 3 scenes reading left to right:
  1. Scene A: standing lord figure (8-Deer name-glyph above head), facing right, holding spear
  2. Place-glyph label: hill form with jaguar-face attribute (= Tilantongo)
  3. Scene B: two figures facing each other; speech scrolls; rope connecting them (= treaty or marriage)
- Background: deer-skin cream (#EFE0B8). Path line: codex red (#A02020). Figures: tan body fills (#D4A870), black outlines

### Example 10 — GLSL Shader: Interlocking Scroll Fill (Veracruz)
- Tile space with `interlockingScroll(uv * 8.0)` at scale 8
- Add SDF-derived relief: height map from scroll distance
- Lighting: raking at 20° angle from top-left
- Pigment-in-recesses: sandstone (#D4B880) on surface, scroll red (#9A2820) in deepest channels
- Animate: slow uniform rotation of the entire scroll pattern (0.05 rad/sec) for hypnotic ritual feel

