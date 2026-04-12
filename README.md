# mesoamerican_style

A structured AI context database for generating accurate, culturally rich Mesoamerican-inspired visual outputs — including shader art, JavaScript generative art, GLSL art, image generation prompts, and related creative work.

---

## What This Repository Is

This is a **context/reference database**, not an app. It is designed to be pulled in as context by AI systems generating Mesoamerican-inspired visual work. Every file is organized for AI consumption: dense, structured, directive.

**Cultures covered:**
- 🐊 **Olmec** — the "mother culture"; sculptural mass; were-jaguar; jade celts; colossal heads
- 🌽 **Teotihuacan** — grid city; Tlaloc goggle eyes; horizontal register murals; talud-tablero
- 🐆 **Zapotec** — Monte Albán; funerary urns; Cocijo rain deity; carved mountain plaza
- 🦅 **Aztec (Mexica)** — codex tradition; Tonalpohualli calendar; featherwork; Sun Stone
- 📜 **Mixtec** — codex strip narrative; gold metalwork; turquoise mosaic; Lord 8-Deer
- 🌳 **Maya** — hieroglyphic writing; Long Count calendar; polychrome ceramics; corbeled temples
- 🐍 **Toltec** — Atlantean warrior columns; Chac Mool; Quetzalcoatl myth; warrior procession friezes
- 🌀 **Totonac / Veracruz (Gulf Coast)** — interlocking scroll; El Tajín niched pyramid; smiling figurines

---

## Repository Structure

```
mesoamerican_style/
│
├── README.md                    # This file
├── CONTEXT_PACK.md              # Overview and recommended reading order
├── STYLE_GUIDE.md               # Core visual principles + culture-specific directives
├── EXAMPLES.md                  # 10 worked generative examples
├── context-pack.json            # Machine-readable index
│
├── cultures/                    # Deep per-culture reference (READ THESE FIRST)
│   ├── aztec.md                 # Aztec/Mexica — glyphs, calendar, motifs, color
│   ├── maya.md                  # Maya — hieroglyphs, Long Count, polychrome, architecture
│   ├── olmec.md                 # Olmec — sculptural mass, were-jaguar, jade, basalt
│   ├── teotihuacan.md           # Teotihuacan — murals, Tlaloc, talud-tablero, city grid
│   ├── zapotec.md               # Zapotec — urns, Monte Albán, Cocijo, step-fret
│   ├── mixtec.md                # Mixtec — codex strips, gold, turquoise mosaic
│   ├── toltec.md                # Toltec — warrior columns, Chac Mool, procession friezes
│   └── totonac_gulf_coast.md   # Veracruz/Totonac — interlocking scroll, niched pyramid
│
├── symbols/                     # Symbol systems and cosmological structures
│   ├── glyphs.json              # Writing systems per culture with generative notes
│   ├── calendars.json           # Calendar systems (Tonalpohualli, Long Count, Sun Stone)
│   ├── cosmology.json           # Cosmological diagrams (quincunx, world tree, 3 levels)
│   └── deities.json             # Major deities with visual attributes
│
├── motifs/
│   └── motifs.json              # 25+ motifs with culture tags, shape notes, generative hints
│
├── palette/
│   └── palettes.json            # 9 culture-specific color palettes with material origins
│
├── materials/
│   └── materials.json           # Stone, pigments, surface treatments with render hints
│
├── architecture/
│   └── architecture.md          # Temple types, profiles, decorative systems per culture
│
├── ceramics/
│   └── ceramics.md              # Ceramic traditions, forms, and decoration per culture
│
├── sculpture/
│   └── sculpture.md             # Relief carving, monument types, technical notes
│
├── prompts/
│   ├── prompt_templates.md      # 25+ culture-specific prompt templates
│   └── negative_prompts.md      # What to avoid (with culture-specific guidance)
│
└── generative/
    ├── shader_hints.md          # GLSL/WebGL modules and lighting models
    └── js_visual_patterns.md    # JavaScript Canvas/SVG pattern generators
```

---

## Recommended Reading Order

For an AI system consuming this repo:

1. **`STYLE_GUIDE.md`** — universal principles + culture quick-reference table
2. **`cultures/[target_culture].md`** — deep reference for the specific culture you're working with
3. **`motifs/motifs.json`** — filter by `cultures` tag for the target culture
4. **`palette/palettes.json`** — select the appropriate culture palette
5. **`symbols/deities.json`** — if deity imagery is needed
6. **`symbols/calendars.json`** — if calendar/cosmological structures are needed
7. **`prompts/prompt_templates.md`** — appropriate template for output type
8. **`prompts/negative_prompts.md`** — what to avoid
9. **`generative/shader_hints.md`** or **`generative/js_visual_patterns.md`** — for code generation
10. **`EXAMPLES.md`** — for worked examples

---

## Quick Reference: Culture → Primary Visual Identity

| Culture        | Signature Form              | Key Motif                    | Palette ID             |
|----------------|-----------------------------|------------------------------|------------------------|
| Aztec          | Codex figure + Sun Stone    | Xicalcoliuhqui scroll        | `aztec_codex`          |
| Maya           | Stela + cylinder vase       | Maya hieroglyph block        | `maya_polychrome`      |
| Olmec          | Colossal head + jade celt   | Were-jaguar cleft face       | `olmec_stone_jade`     |
| Teotihuacan    | Mural register composition  | Tlaloc goggle eyes           | `teotihuacan_mural`    |
| Zapotec        | Funerary urn                | Cocijo bifurcated tongue     | `zapotec_urn`          |
| Mixtec         | Codex strip narrative       | Red-path reading line        | `mixtec_codex`         |
| Toltec         | Atlantean warrior column    | Warrior procession frieze    | `stone_jade_cinnabar`  |
| Veracruz       | Niched pyramid + scroll     | Interlocking double scroll   | `gulf_coast_scroll`    |

---

## Version

**Pack version:** 1.0.0  
**Cultures covered:** 8  
**Motifs catalogued:** 25+  
**Palettes:** 9  
**Deities documented:** 11  
**Calendar systems:** 6  

